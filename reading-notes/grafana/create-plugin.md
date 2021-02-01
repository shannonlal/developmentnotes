# Notes from the following file
https://grafana.com/tutorials/build-a-data-source-backend-plugin/#1

## Environment
1. Create a directory called grafana-plugins
2. Find the plugins property in the Grafana configureation file set the plugins property to our directory

## Create the plugin

# Grafana Toolkit
https://github.com/grafana/grafana/tree/master/packages/grafana-toolkit


# Anatomy of backend plugin

## plugin.json
-- type: panel, datasources and app
-- name: 
-- id

## module.ts
- entrypoint for plugin

# Datasource API
-- define two methods
query

```
async query(options: DataQueryRequest<MyQuery>): Promise<DataQueryResponse>

NOTE: options contains the targets along with context information
```
testDatasource

```
async testDatasource()
```

# Datea frames


# Query Editory
- Query Model.  Defines the user input of your data source
src/types.ts
```
export interface MyQuery extends DataQuery {
  queryText?: string;
  constant: number;
  frequency: number;
}
```

Add support for variables in plugins


const query = getTemplateSrv().replace('SELECT * FROM services WHERE id = "$service"', options.scopedVars);

Update the variables from a plugin

## Query Variables Supports

```
export interface MyVariableQuery {
  namespace: string;
  rawQuery: string;
}
```

## Logs datasource
-add logs to true for plugin.json

## Must use dataframe
- Stores columnar-oriented table structure.  Data is a collection of fields where each field corresponds to a column.  Each field, in turn consits ofa collection of values along with meta information


```
interface Field {
    name:    string;
     // Prometheus like Labels / Tags
    labels?: Record<string, string>;

    // For example string, number, time (or more specific primitives in the backend)
    type:   FieldType;
    // Array of values all of the same type
    values: Vector<T>;

    // Optional display data for the field (e.g. unit, name over-ride, etc)
    config: FieldConfig;
}
```

# Configure a Data Soruce
