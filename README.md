OpenShift Kibana Cartridge
=================================
This cartridge provides a Kibana 4.0 dashboard. A health check url is also configured and is on `/health`.

To create your Kibana app, run:

    rhc app-create https://raw.githubusercontent.com/abraverm/openshift-kibana/master/metadata/manifest.yml -e elasticsearch.conf  -a <app>

### Configuration
`elasticsearch.conf` is a file containing environment variables used for generating  kibana.conf:

    ES_URL=my.es.host.com
    ES_PORT=9200
    ES_USERNAME=myuser
    ES_PASSWORD=mypassword

Required variables: `ES_URL` and `ES_PORT`

### Updates

Only Kibana is upgradeable. The setup looks at an environment variable to handle the upgrade.

The steps are as follows:

  - rhc set-env KIBANA_VERSION=4.0.2 -a <app> --namespace <domain>
  - trigger a `deploy` by pushing a change with git

Note: only Kibana 4 is supported by this cartridge

### License
This cartridge is [MIT](http://opensource.org/licenses/MIT) licensed.
