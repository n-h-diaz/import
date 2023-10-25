# Importer Config

The config parameters for the files to be imported should be specified in a `config.json` file.

## Sample `config.json`

```json
{
  "inputFiles": {
    "countries.csv": {
      "entityType": "Country",
      "ignoreColumns": ["ignore1", "ignore2"]
    },
    "latlng.csv": {
      "entityType": "State"
    },
    "geoid.csv": {
      "entityType": ""
    }
  },
  "variables": {
    "Variable 1": {"group": "Parent Group/Child Group 1"},
    "Variable 2": {"group": "Parent Group/Child Group 1"},
    "var3": {
      "name": "Var 3 Name",
      "description": "Var 3 Description",
      "nlSentences": ["Sentence 1", "Sentence 2"],
      "group": "Parent Group/Child Group 2",
    },
  }
}
```

## `inputFiles`

The top-level `inputFiles` field should encode a map from input file name to parameters specific to that file.

### Input file parameters

#### `entityType`

All entities in a given file must be of a specific type. This type should be
specified as the value of the `entityType` field. The importer tries to resolve
entities to dcids of that type.

#### `ignoreColumns`

The list of column names to be ignored by the importer, if any.

## `variables`

The top-level `variables` field can be used to provide more information about variables 
in the input CSVs.

If not specified, the variable column names in the CSVs will be used as their names.

Names can be overriden and other information can be provided using the parameters described below.

### Variable parameters

#### `name`

The display name of the variable.
If not specified, the column name will be used as the display name.

#### `description`

The long form description of the variable.

The description will also be used to create NL embeddings for the variable.

#### `group`

Variables can be arranged in groups.
The group hierarchy can be specified using the `group` property.
Use "/" as a separator to specify a multi-level hierarchy.

#### `nlSentences`

An array of NL sentences to be used for creating more NL embeddings (in addition to the description)
for the variable.