# SETUP NOTES
The following are quick setup notes. The main goal of this is to get familiar with installing plugins and eventually connect to github


# Grafana CLI

## Notes
grafana-cli --pluginDir does not permantly change the location

### Override Default Plugin Directory
--pluginsDir temporarly overrides the local grafana instance stores the plugins.

--repo
grafana-cli --repo allows you to install plugin from a repo
Question: Can you do this from git

```
grafana-cli --repo "https://example.com/plugins" plugins install <plugin-id>
```

Example
```
grafana-cli --pluginUrl https://company.com/grafana/plugins/<plugin-id>-<plugin-version>.zip plugins install <plugin-id>
```

### Enable Debugging
```
--deubg or -d
```

Output is displayed in terminal

Example

```
grafana-cli --debug plugins install <plugin-id>

```

## Plugin Commands

### List available plugins
```
grafana-cli plugins list-remote
```

### Reset Admin Password

```
grafana-cli admin
```




### Install plugin by ID

# Simple JSON Datasource

# Install Github Plugin

# Setting up Grafana for High Availability
https://grafana.com/docs/grafana/latest/administration/set-up-for-high-availability/

- Must use Postgres or Mysql
- Alerts are duplicated across multiple servers but alert only sent once