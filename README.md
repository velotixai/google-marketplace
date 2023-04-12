# [WIP] Velotix Application on Google Marketplace

## Prerequisites 

* Wildcard SSL for your domain

* DNS records for:

`velotix.mydomain.com` - The main site for Velotix interface

`velotix-be.mydomain.com` - The backend of Velotix

`velotix-se.mydomain.com` - Superset service for Velotix dashboards

`velotix-ke.mydomain.com` - Keycloak service for Velotix User Federation

# TBD

# velotix-mp

![Version: 1.0.0](https://img.shields.io/badge/Version-1.0.0-informational?style=flat-square)

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| suite.aidataengineer.image.repository | string | `nil` |  |
| suite.aidataengineer.image.tag | string | `nil` |  |
| suite.aidataengineer.initContainers[0].command[0] | string | `"/bin/sh"` |  |
| suite.aidataengineer.initContainers[0].command[1] | string | `"-c"` |  |
| suite.aidataengineer.initContainers[0].command[2] | string | `"dockerize -wait \"http://nats:8222/\" -timeout 120s"` |  |
| suite.aidataengineer.initContainers[0].image | string | `"gcr.io/velotix-public/velotix/dockerize:0.5.0"` |  |
| suite.aidataengineer.initContainers[0].imagePullPolicy | string | `"Always"` |  |
| suite.aidataengineer.initContainers[0].name | string | `"wait-for-nats"` |  |
| suite.aidataengineer.initContainers[1].command[0] | string | `"/bin/sh"` |  |
| suite.aidataengineer.initContainers[1].command[1] | string | `"-c"` |  |
| suite.aidataengineer.initContainers[1].command[2] | string | `"dockerize -wait \"tcp://mysql:3306/\" -timeout 120s"` |  |
| suite.aidataengineer.initContainers[1].image | string | `"gcr.io/velotix-public/velotix/dockerize:0.5.0"` |  |
| suite.aidataengineer.initContainers[1].imagePullPolicy | string | `"IfNotPresent"` |  |
| suite.aidataengineer.initContainers[1].name | string | `"wait-for-mysql"` |  |
| suite.aiengine.image.repository | string | `nil` |  |
| suite.aiengine.image.tag | string | `nil` |  |
| suite.aiengine.initContainers[0].command[0] | string | `"/bin/sh"` |  |
| suite.aiengine.initContainers[0].command[1] | string | `"-c"` |  |
| suite.aiengine.initContainers[0].command[2] | string | `"dockerize -wait \"http://ai-data-engineer:5000/system/status\" -timeout 240s"` |  |
| suite.aiengine.initContainers[0].image | string | `"gcr.io/velotix-public/velotix/dockerize:0.5.0"` |  |
| suite.aiengine.initContainers[0].imagePullPolicy | string | `"Always"` |  |
| suite.aiengine.initContainers[0].name | string | `"wait-for-aidataengineer"` |  |
| suite.auditlogreader.image.repository | string | `nil` |  |
| suite.auditlogreader.image.tag | string | `nil` |  |
| suite.client.extraEnv.APP_API_URL | string | `"https://{{ .Values.global.ingress.subDomains.fe }}{{ .Values.global.ingress.wildcardDomain }}"` |  |
| suite.client.extraEnv.APP_KEYCLOAK_URL | string | `"https://{{ .Values.global.ingress.subDomains.keycloak }}{{ .Values.global.ingress.wildcardDomain }}"` |  |
| suite.client.extraEnv.APP_SUPERSET_DOMAIN | string | `"https://{{ .Values.global.ingress.subDomains.superset }}{{ .Values.global.ingress.wildcardDomain }}"` |  |
| suite.client.image.repository | string | `nil` |  |
| suite.client.image.tag | string | `nil` |  |
| suite.datahub.acryl-datahub-actions.image.pullPolicy | string | `"Always"` |  |
| suite.datahub.acryl-datahub-actions.image.repository | string | `nil` |  |
| suite.datahub.acryl-datahub-actions.image.tag | string | `nil` |  |
| suite.datahub.cp-helm-charts.cp-schema-registry.image | string | `nil` |  |
| suite.datahub.cp-helm-charts.cp-schema-registry.imagePullPolicy | string | `"Always"` |  |
| suite.datahub.cp-helm-charts.cp-schema-registry.imageTag | string | `nil` |  |
| suite.datahub.datahub-frontend.image.pullPolicy | string | `"Always"` |  |
| suite.datahub.datahub-frontend.image.repository | string | `nil` |  |
| suite.datahub.datahub-frontend.image.tag | string | `nil` |  |
| suite.datahub.datahub-gms.image.pullPolicy | string | `"Always"` |  |
| suite.datahub.datahub-gms.image.repository | string | `nil` |  |
| suite.datahub.datahub-gms.image.tag | string | `nil` |  |
| suite.datahub.datahub-gms.initContainers[0].command[0] | string | `"sh"` |  |
| suite.datahub.datahub-gms.initContainers[0].command[1] | string | `"-c"` |  |
| suite.datahub.datahub-gms.initContainers[0].command[2] | string | `"{{- if or .Release.IsInstall .Release.IsUpgrade .Release.IsRollback }}\necho \"Waiting for {{ .Release.Name }}-datahub-system-update-job\"\nkubectl wait --for=condition=complete job/{{ .Release.Name }}-datahub-system-update-job --timeout=360s\n{{- end }}\n"` |  |
| suite.datahub.datahub-gms.initContainers[0].image | string | `"gcr.io/velotix-public/velotix/kubectl:0.5.0"` |  |
| suite.datahub.datahub-gms.initContainers[0].imagePullPolicy | string | `"Always"` |  |
| suite.datahub.datahub-gms.initContainers[0].name | string | `"wait-for-system-update"` |  |
| suite.datahub.datahubSystemUpdate.image.pullPolicy | string | `"Always"` |  |
| suite.datahub.datahubSystemUpdate.image.repository | string | `nil` |  |
| suite.datahub.datahubSystemUpdate.image.tag | string | `nil` |  |
| suite.datahub.datahubSystemUpdate.initContainers[0].command[0] | string | `"sh"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[0].command[1] | string | `"-c"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[0].command[2] | string | `"echo \"Waiting for {{ .Release.Name }}-elasticsearch-setup-job\"\nkubectl wait --for=condition=complete job/{{ .Release.Name }}-elasticsearch-setup-job --timeout=300s\n"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[0].image | string | `"gcr.io/velotix-public/velotix/kubectl:0.5.0"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[0].imagePullPolicy | string | `"Always"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[0].name | string | `"wait-for-elasticsearch-setup"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[1].command[0] | string | `"sh"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[1].command[1] | string | `"-c"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[1].command[2] | string | `"echo \"Waiting for {{ .Release.Name }}-kafka-setup-job\"\nkubectl wait --for=condition=complete job/{{ .Release.Name }}-kafka-setup-job --timeout=300s\n"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[1].image | string | `"gcr.io/velotix-public/velotix/kubectl:0.5.0"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[1].imagePullPolicy | string | `"Always"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[1].name | string | `"wait-for-kafka-setup"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[2].command[0] | string | `"sh"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[2].command[1] | string | `"-c"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[2].command[2] | string | `"{{- if contains \"mysql\" .Values.global.sql.datasource.driver }}\necho \"Waiting for {{ .Release.Name }}-mysql-setup-job\"\nkubectl wait --for=condition=complete job/{{ .Release.Name }}-mysql-setup-job --timeout=300s\n{{ else if contains \"postgresql\" .Values.global.sql.datasource.driver }}\necho \"Waiting for {{ .Release.Name }}-postgresql-setup-job\"\nkubectl wait --for=condition=complete job/{{ .Release.Name }}-postgresql-setup-job --timeout=300s\n{{- end }}\n"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[2].image | string | `"gcr.io/velotix-public/velotix/kubectl:0.5.0"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[2].imagePullPolicy | string | `"Always"` |  |
| suite.datahub.datahubSystemUpdate.initContainers[2].name | string | `"wait-for-database-setup"` |  |
| suite.datahub.datahubUpgrade.image.pullPolicy | string | `"Always"` |  |
| suite.datahub.datahubUpgrade.image.repository | string | `nil` |  |
| suite.datahub.datahubUpgrade.image.tag | string | `nil` |  |
| suite.datahub.datahubUpgrade.initContainers[0].command[0] | string | `"sh"` |  |
| suite.datahub.datahubUpgrade.initContainers[0].command[1] | string | `"-c"` |  |
| suite.datahub.datahubUpgrade.initContainers[0].command[2] | string | `"export datahubGmsHost={{ printf \"%s:%s\" (printf \"%s-%s\" .Release.Name \"datahub-gms\") \"8080\" }}\nuntil curl -I --connect-timeout 5 http://${datahubGmsHost}/health; do\n  echo \"Waiting for http://${datahubGmsHost}/health\";\ndone;\n"` |  |
| suite.datahub.datahubUpgrade.initContainers[0].image | string | `"gcr.io/velotix-public/velotix/curl:0.5.0"` |  |
| suite.datahub.datahubUpgrade.initContainers[0].imagePullPolicy | string | `"Always"` |  |
| suite.datahub.datahubUpgrade.initContainers[0].name | string | `"wait-for-datahub-gms"` |  |
| suite.datahub.elasticsearch.image | string | `nil` |  |
| suite.datahub.elasticsearch.imagePullPolicy | string | `"Always"` |  |
| suite.datahub.elasticsearch.imageTag | string | `nil` |  |
| suite.datahub.elasticsearchSetupJob.image.pullPolicy | string | `"Always"` |  |
| suite.datahub.elasticsearchSetupJob.image.repository | string | `nil` |  |
| suite.datahub.elasticsearchSetupJob.image.tag | string | `nil` |  |
| suite.datahub.kafka.image.pullPolicy | string | `"Always"` |  |
| suite.datahub.kafka.image.registry | string | `nil` |  |
| suite.datahub.kafka.image.repository | string | `nil` |  |
| suite.datahub.kafka.image.tag | string | `nil` |  |
| suite.datahub.kafka.initContainers[0].command[0] | string | `"/bin/sh"` |  |
| suite.datahub.kafka.initContainers[0].command[1] | string | `"-c"` |  |
| suite.datahub.kafka.initContainers[0].command[2] | string | `"dockerize -wait \"tcp://{{ .Values.global.kafka.zookeeper.server }}/\" -timeout 360s"` |  |
| suite.datahub.kafka.initContainers[0].image | string | `"gcr.io/velotix-public/velotix/dockerize:0.5.0"` |  |
| suite.datahub.kafka.initContainers[0].imagePullPolicy | string | `"Always"` |  |
| suite.datahub.kafka.initContainers[0].name | string | `"wait-for-zookeeper"` |  |
| suite.datahub.kafka.zookeeper.image.pullPolicy | string | `"Always"` |  |
| suite.datahub.kafka.zookeeper.image.registry | string | `nil` |  |
| suite.datahub.kafka.zookeeper.image.repository | string | `nil` |  |
| suite.datahub.kafka.zookeeper.image.tag | string | `nil` |  |
| suite.datahub.kafkaSetupJob.image.pullPolicy | string | `"Always"` |  |
| suite.datahub.kafkaSetupJob.image.repository | string | `nil` |  |
| suite.datahub.kafkaSetupJob.image.tag | string | `nil` |  |
| suite.datahub.kafkaSetupJob.initContainers[0].command[0] | string | `"/bin/sh"` |  |
| suite.datahub.kafkaSetupJob.initContainers[0].command[1] | string | `"-c"` |  |
| suite.datahub.kafkaSetupJob.initContainers[0].command[2] | string | `"dockerize -wait \"tcp://{{ .Values.global.kafka.bootstrap.server | quote }}/\" -timeout 360s"` |  |
| suite.datahub.kafkaSetupJob.initContainers[0].image | string | `"gcr.io/velotix-public/velotix/dockerize:0.5.0"` |  |
| suite.datahub.kafkaSetupJob.initContainers[0].imagePullPolicy | string | `"Always"` |  |
| suite.datahub.kafkaSetupJob.initContainers[0].name | string | `"wait-for-kafka"` |  |
| suite.datahub.mysql.image.pullPolicy | string | `"Always"` |  |
| suite.datahub.mysql.image.registry | string | `nil` |  |
| suite.datahub.mysql.image.repository | string | `nil` |  |
| suite.datahub.mysql.image.tag | string | `nil` |  |
| suite.datahub.postgresql.image.pullPolicy | string | `"Always"` |  |
| suite.datahub.postgresql.image.registry | string | `nil` |  |
| suite.datahub.postgresql.image.repository | string | `nil` |  |
| suite.datahub.postgresql.image.tag | string | `nil` |  |
| suite.datahub.postgresqlSetupJob.image.pullPolicy | string | `"Always"` |  |
| suite.datahub.postgresqlSetupJob.image.repository | string | `nil` |  |
| suite.datahub.postgresqlSetupJob.image.tag | string | `nil` |  |
| suite.datasourcemanager.image.repository | string | `nil` |  |
| suite.datasourcemanager.image.tag | string | `nil` |  |
| suite.datasourcemanager.initContainers[0].command[0] | string | `"/bin/sh"` |  |
| suite.datasourcemanager.initContainers[0].command[1] | string | `"-c"` |  |
| suite.datasourcemanager.initContainers[0].command[2] | string | `"dockerize -wait \"http://nats:8222/\" -timeout 120s"` |  |
| suite.datasourcemanager.initContainers[0].image | string | `"gcr.io/velotix-public/velotix/dockerize:0.5.0"` |  |
| suite.datasourcemanager.initContainers[0].imagePullPolicy | string | `"Always"` |  |
| suite.datasourcemanager.initContainers[0].name | string | `"wait-for-nats"` |  |
| suite.envcontrol.enabled | bool | `false` |  |
| suite.fe.configMap.data.CLIENT_BASE_URL | string | `"https://{{ .Values.global.ingress.subDomains.client }}{{ .Values.global.ingress.wildcardDomain }}"` |  |
| suite.fe.configMap.data.FE_BASE_URL | string | `"https://{{ .Values.global.ingress.subDomains.fe }}{{ .Values.global.ingress.wildcardDomain }}"` |  |
| suite.fe.configMap.data.FE_CLIENT_UUID | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_ADMIN_PASS | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_ADMIN_USER | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_SERVER_URL | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_UFED_BIND_CREDENTIAL | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_UFED_BIND_DN | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_UFED_CONNECTION_URL | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_UFED_ENABLED | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_UFED_USERS_DN | string | `nil` |  |
| suite.fe.configMap.data.KEYCLOAK_UFED_VENDOR | string | `nil` |  |
| suite.fe.image.repository | string | `nil` |  |
| suite.fe.image.tag | string | `nil` |  |
| suite.fe.initContainers[0].command[0] | string | `"/bin/sh"` |  |
| suite.fe.initContainers[0].command[1] | string | `"-c"` |  |
| suite.fe.initContainers[0].command[2] | string | `"dockerize -wait \"http://nats:8222/\" -timeout 120s"` |  |
| suite.fe.initContainers[0].image | string | `"gcr.io/velotix-public/velotix/dockerize:0.5.0"` |  |
| suite.fe.initContainers[0].imagePullPolicy | string | `"Always"` |  |
| suite.fe.initContainers[0].name | string | `"wait-for-nats"` |  |
| suite.fe.initContainers[1].command[0] | string | `"/bin/sh"` |  |
| suite.fe.initContainers[1].command[1] | string | `"-c"` |  |
| suite.fe.initContainers[1].command[2] | string | `"dockerize -wait \"tcp://mysql:3306/\" -timeout 120s"` |  |
| suite.fe.initContainers[1].image | string | `"gcr.io/velotix-public/velotix/dockerize:0.5.0"` |  |
| suite.fe.initContainers[1].imagePullPolicy | string | `"Always"` |  |
| suite.fe.initContainers[1].name | string | `"wait-for-mysql"` |  |
| suite.fe.initContainers[2].envFrom[0].configMapRef.name | string | `"fe-configmap"` |  |
| suite.fe.initContainers[2].image | string | `"gcr.io/velotix-public/velotix/init-keycloak:0.5.0"` |  |
| suite.fe.initContainers[2].imagePullPolicy | string | `"Always"` |  |
| suite.fe.initContainers[2].name | string | `"init-keycloak"` |  |
| suite.fe.springApplicationJson.config.app.encryption.iv | string | `nil` |  |
| suite.fe.springApplicationJson.config.app.encryption.secret | string | `nil` |  |
| suite.fe.springApplicationJson.config.app.internal-operations.enabled | bool | `false` |  |
| suite.fe.springApplicationJson.config.app.jwt.secret | string | `nil` |  |
| suite.fe.springApplicationJson.config.app.superset.base-url | string | `"https://{{ .Values.global.ingress.subDomains.superset }}{{ .Values.global.ingress.wildcardDomain }}"` |  |
| suite.fe.springApplicationJson.enabled | bool | `true` |  |
| suite.global.image.pullPolicy | string | `"Always"` |  |
| suite.global.image.registry | string | `"gcr.io"` |  |
| suite.global.imagePullSecrets | list | `[]` |  |
| suite.global.ingress.enabled | string | `nil` |  |
| suite.global.ingress.subDomains.client | string | `nil` |  |
| suite.global.ingress.subDomains.fe | string | `nil` |  |
| suite.global.ingress.subDomains.keycloak | string | `nil` |  |
| suite.global.ingress.subDomains.superset | string | `nil` |  |
| suite.global.ingress.wildcardCert | string | `nil` |  |
| suite.global.ingress.wildcardCertKey | string | `nil` |  |
| suite.global.ingress.wildcardDomain | string | `nil` |  |
| suite.keycloak.extraEnv.KEYCLOAK_FRONTEND_URL | string | `""` |  |
| suite.keycloak.image.pullPolicy | string | `"Always"` |  |
| suite.keycloak.image.repository | string | `nil` |  |
| suite.keycloak.image.tag | string | `nil` |  |
| suite.nats.nats.image.pullPolicy | string | `"Always"` |  |
| suite.nats.nats.image.registry | string | `nil` |  |
| suite.nats.nats.image.repository | string | `nil` |  |
| suite.nats.nats.image.tag | string | `nil` |  |
| suite.nats.natsbox.image.pullPolicy | string | `"Always"` |  |
| suite.nats.natsbox.image.registry | string | `nil` |  |
| suite.nats.natsbox.image.repository | string | `nil` |  |
| suite.nats.natsbox.image.tag | string | `nil` |  |
| suite.presidio.image.repository | string | `nil` |  |
| suite.presidio.image.tag | string | `nil` |  |
| suite.prometheus.server.image.pullPolicy | string | `"Always"` |  |
| suite.prometheus.server.image.repository | string | `nil` |  |
| suite.prometheus.server.image.tag | string | `nil` |  |
| suite.propengine.image.repository | string | `nil` |  |
| suite.propengine.image.tag | string | `nil` |  |
| suite.propengine.initContainers[0].command[0] | string | `"/bin/sh"` |  |
| suite.propengine.initContainers[0].command[1] | string | `"-c"` |  |
| suite.propengine.initContainers[0].command[2] | string | `"dockerize -wait \"http://ai-data-engineer:5000/system/status\" -timeout 240s"` |  |
| suite.propengine.initContainers[0].image | string | `"gcr.io/velotix-public/velotix/dockerize:0.5.0"` |  |
| suite.propengine.initContainers[0].imagePullPolicy | string | `"Always"` |  |
| suite.propengine.initContainers[0].name | string | `"wait-for-aidataengineer"` |  |
| suite.rabbitmq.auth.erlangCookie | string | `nil` |  |
| suite.rabbitmq.image.pullPolicy | string | `"Always"` |  |
| suite.rabbitmq.image.registry | string | `nil` |  |
| suite.rabbitmq.image.repository | string | `nil` |  |
| suite.rabbitmq.image.tag | string | `nil` |  |
| suite.registryCredentials.createSecret | bool | `false` |  |
| suite.superset.image.pullPolicy | string | `"Always"` |  |
| suite.superset.image.repository | string | `nil` |  |
| suite.superset.image.tag | string | `nil` |  |
| suite.superset.initImage.pullPolicy | string | `"Always"` |  |
| suite.superset.initImage.repository | string | `"gcr.io/velotix-public/velotix/dockerize"` |  |
| suite.superset.initImage.tag | string | `nil` |  |
| suite.superset.redis.image.pullPolicy | string | `"Always"` |  |
| suite.superset.redis.image.registry | string | `nil` |  |
| suite.superset.redis.image.repository | string | `nil` |  |
| suite.superset.redis.image.tag | string | `nil` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
