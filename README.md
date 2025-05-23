# Snowflake DBML Generator

The Snowflake DBML Generator is an open-source tool that translates Snowflake database schemas into DBML (Database Markup Language), facilitating easy generation of ER diagrams and comprehensive documentation of database structures. 

For data engineers, analysts, and ML engineers, it enables you to bootstrap a rich interactive DB diagram directly from Snowflake.

![Demo Install and Usage](docs/images/demo-final.svg)

## Quick Start

```bash
pip install snowflake-dbml-generator
snowflake-dbml --interactive
```

## Examples

Using [Snowflake's Sample Data Sets](https://docs.snowflake.com/en/user-guide/sample-data), here are demonstrations of generating DBML and visualizing it with dbdiagram.io:

### 1. Snowflake TPCH SF100 Dataset

![TPCH SF100 Dataset Diagram](docs/images/dbdocs_Sample_TPCH_SF100.svg)
- [ER Diagram on dbdiagram.io](https://dbdiagram.io/d/snowflake_sample-TPCH_SF100-6631d8395b24a634d03a1d8e)
- [Snowflake Dataset Documentation](https://docs.snowflake.com/en/user-guide/sample-data-tpch.html)

### 2. Snowflake TPCDS SF100TCL Dataset
![TPCDS SF100TCL Dataset Diagram](docs/images/dbdocs_Sample_TPCDS_SF100TCL.svg)

- [ER Diagram on dbdiagram.io](https://dbdiagram.io/d/snowflake_sample-tpcds_sf100tcl-6631078d5b24a634d02fbd57)
- [Snowflake Dataset Documentation](https://docs.snowflake.com/en/user-guide/sample-data-tpcds.html)

## Features

- **Automatic DBML Generation**: Converts Snowflake schema definitions into DBML automatically.
- **Complex Schema Support**: Manages complex relationships, including composite foreign keys.
- **Interactive Mode**: Guides through configuration file generation and database connection setup.
- **Customizable Visualization**: Allows customization of DBML file appearances with configurable color schemes.
- **SQL Comments Extraction**: Extracts SQL table and column comments as DBML notes.
- **Table Statistics**: Includes table statistics like row count and size in bytes in the DBML output.

## Installation

### Prerequisites
- Python 3.6+
- Snowflake account credentials

### Install from PyPI
```bash
pip install snowflake-dbml-generator
```

### Build from Source
```bash
git clone https://github.com/ryanrozich/snowflake-dbml-generator.git
cd snowflake-dbml-generator
python -m venv venv
.\venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

## Usage

### Command Line Interface
Run the generator via the command line. For detailed usage, see [Configuration Parameters](docs/Configuration_Parameters.md).

```bash
snowflake-dbml --user <username> --password <password> --account <account_id> --warehouse <warehouse> --database <database> --role <role>
```

### Interactive Mode
For guided setup:

```bash
snowflake-dbml --interactive
```

## Configuration Parameters

Configuration can be set via environment variables, a `.env` file, or command-line arguments. [Learn more about setting configuration parameters.](docs/Configuration_Parameters.md)

## Configuration File

For advanced setups, particularly when Snowflake does not enforce foreign key relationships, a `config.json` file can define how relationships are inferred. See [Configuring Relationships](docs/Configuring_Relationships.md) for detailed setup.

### Generating DBML

To generate a DBML file after setting up your configuration:

```bash
snowflake-dbml --config-file config.json > output.dbml
```

## Contributing

Contributions are welcome! Whether it's tweaking code, enhancing documentation, or reporting bugs, we'd love to see your pull requests. Let's make this tool even better together!

Here’s a refined section for your `README.md` to document all special commit message keywords, including instructions for controlling version increments. This section can be integrated into your GitHub repository documentation:

### Commit Message Keywords

In our continuous integration process, commit message keywords play a crucial role in determining the nature of changes and the corresponding actions in our deployment pipeline. Below are the keywords that you can use to control versioning and deployment:

#### Keywords:

- **`[skip version]`**
  - **Purpose**: Prevents any version bump or tag creation. Use this keyword for commits that make non-functional changes, such as updates to documentation, that do not warrant a new version number.
  - **Example**:
    ```bash
    git commit -m "Update README [skip version]"
    ```

- **`MAJOR:`**
  - **Purpose**: Triggers a major version bump, indicating backward-incompatible changes that require this level of escalation.
  - **Example**:
    ```bash
    git commit -m "MAJOR: Redesign database schema for scalability"
    ```

- **`MINOR:`**
  - **Purpose**: Triggers a minor version bump, suitable for backward-compatible functionality enhancements.
  - **Example**:
    ```bash
    git commit -m "MINOR: Add new analytics features"
    ```

- **`PATCH:`** (default if no keyword is specified)
  - **Purpose**: Applies a patch version bump, typically for bug fixes and minor changes that don’t add new features or break existing ones.
  - **Example**:
    ```bash
    git commit -m "PATCH: Fix data loading issue"
    ```

#### Workflow Integration:

These keywords are evaluated in our GitHub Actions workflow to decide the type of version bump or to skip versioning entirely. It ensures that our versioning reflects the nature of changes accurately, maintaining consistency and predictability in our release process.

By using these keywords appropriately in your commit messages, you help maintain the integrity of the versioning process and ensure that each release is meaningful.

## License

Licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

Ryan Rozich - [GitHub](https://github.com/ryanrozich)

## Acknowledgments