# jenkins

![Version: 4.3.1-bb.1](https://img.shields.io/badge/Version-4.3.1--bb.1-informational?style=flat-square) ![AppVersion: 2.390](https://img.shields.io/badge/AppVersion-2.390-informational?style=flat-square)

Jenkins - Build great things at any scale! The leading open source automation server, Jenkins provides hundreds of plugins to support building, deploying and automating any project.

## Upstream References
* <https://jenkins.io/>

* <https://github.com/jenkinsci/jenkins>
* <https://github.com/jenkinsci/docker-inbound-agent>
* <https://github.com/maorfr/kube-tasks>
* <https://github.com/jenkinsci/configuration-as-code-plugin>

## Learn More
* [Application Overview](docs/overview.md)
* [Other Documentation](docs/)

## Pre-Requisites

* Kubernetes Cluster deployed
* Kubernetes config installed in `~/.kube/config`
* Helm installed

Install Helm

https://helm.sh/docs/intro/install/

## Deployment

* Clone down the repository
* cd into directory
```bash
helm install jenkins chart/
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| clusterZone | string | `"cluster.local"` |  |
| renderHelmLabels | bool | `true` |  |
| controller.componentName | string | `"jenkins-controller"` |  |
| controller.image | string | `"registry1.dso.mil/ironbank/opensource/jenkins/jenkins"` |  |
| controller.tag | string | `"2.390"` |  |
| controller.imagePullPolicy | string | `"Always"` |  |
| controller.imagePullSecretName | string | `"private-registry"` |  |
| controller.lifecycle | string | `nil` |  |
| controller.disableRememberMe | bool | `false` |  |
| controller.numExecutors | int | `0` |  |
| controller.executorMode | string | `"NORMAL"` |  |
| controller.markupFormatter | string | `"plainText"` |  |
| controller.customJenkinsLabels | list | `[]` |  |
| controller.adminSecret | bool | `true` |  |
| controller.hostNetworking | bool | `false` |  |
| controller.adminUser | string | `"admin"` |  |
| controller.admin.existingSecret | string | `""` |  |
| controller.admin.userKey | string | `"jenkins-admin-user"` |  |
| controller.admin.passwordKey | string | `"jenkins-admin-password"` |  |
| controller.jenkinsHome | string | `"/var/jenkins_home"` |  |
| controller.jenkinsRef | string | `"/usr/share/jenkins/ref"` |  |
| controller.jenkinsWar | string | `"/usr/share/jenkins/jenkins.war"` |  |
| controller.resources.requests.cpu | string | `"500m"` |  |
| controller.resources.requests.memory | string | `"1024Mi"` |  |
| controller.resources.limits.cpu | string | `"500m"` |  |
| controller.resources.limits.memory | string | `"1024Mi"` |  |
| controller.javaOpts | string | `"-Xms512m -Xmx512m -Dcom.redhat.fips=false"` |  |
| controller.usePodSecurityContext | bool | `true` |  |
| controller.runAsUser | int | `1000` |  |
| controller.fsGroup | int | `1000` |  |
| controller.securityContextCapabilities.drop[0] | string | `"ALL"` |  |
| controller.containerSecurityContext.runAsUser | int | `1000` |  |
| controller.containerSecurityContext.runAsGroup | int | `1000` |  |
| controller.containerSecurityContext.readOnlyRootFilesystem | bool | `true` |  |
| controller.containerSecurityContext.allowPrivilegeEscalation | bool | `false` |  |
| controller.servicePort | int | `8080` |  |
| controller.targetPort | int | `8080` |  |
| controller.serviceType | string | `"ClusterIP"` |  |
| controller.serviceExternalTrafficPolicy | string | `nil` |  |
| controller.serviceAnnotations | object | `{}` |  |
| controller.statefulSetLabels | object | `{}` |  |
| controller.serviceLabels | object | `{}` |  |
| controller.podLabels | object | `{}` |  |
| controller.healthProbes | bool | `true` |  |
| controller.probes.startupProbe.httpGet.path | string | `"{{ default \"\" .Values.controller.jenkinsUriPrefix }}/login"` |  |
| controller.probes.startupProbe.httpGet.port | string | `"http"` |  |
| controller.probes.startupProbe.periodSeconds | int | `10` |  |
| controller.probes.startupProbe.timeoutSeconds | int | `5` |  |
| controller.probes.startupProbe.failureThreshold | int | `12` |  |
| controller.probes.livenessProbe.failureThreshold | int | `5` |  |
| controller.probes.livenessProbe.httpGet.path | string | `"{{ default \"\" .Values.controller.jenkinsUriPrefix }}/login"` |  |
| controller.probes.livenessProbe.httpGet.port | string | `"http"` |  |
| controller.probes.livenessProbe.periodSeconds | int | `10` |  |
| controller.probes.livenessProbe.timeoutSeconds | int | `5` |  |
| controller.probes.readinessProbe.failureThreshold | int | `3` |  |
| controller.probes.readinessProbe.httpGet.path | string | `"{{ default \"\" .Values.controller.jenkinsUriPrefix }}/login"` |  |
| controller.probes.readinessProbe.httpGet.port | string | `"http"` |  |
| controller.probes.readinessProbe.periodSeconds | int | `10` |  |
| controller.probes.readinessProbe.timeoutSeconds | int | `5` |  |
| controller.podDisruptionBudget.enabled | bool | `false` |  |
| controller.podDisruptionBudget.apiVersion | string | `"policy/v1beta1"` |  |
| controller.podDisruptionBudget.annotations | object | `{}` |  |
| controller.podDisruptionBudget.labels | object | `{}` |  |
| controller.agentListenerEnabled | bool | `true` |  |
| controller.agentListenerPort | int | `50000` |  |
| controller.agentListenerHostPort | string | `nil` |  |
| controller.agentListenerNodePort | string | `nil` |  |
| controller.agentListenerExternalTrafficPolicy | string | `nil` |  |
| controller.agentListenerLoadBalancerSourceRanges[0] | string | `"0.0.0.0/0"` |  |
| controller.disabledAgentProtocols[0] | string | `"JNLP-connect"` |  |
| controller.disabledAgentProtocols[1] | string | `"JNLP2-connect"` |  |
| controller.csrf.defaultCrumbIssuer.enabled | bool | `true` |  |
| controller.csrf.defaultCrumbIssuer.proxyCompatability | bool | `true` |  |
| controller.agentListenerServiceType | string | `"ClusterIP"` |  |
| controller.agentListenerLoadBalancerIP | string | `nil` |  |
| controller.agentListenerServiceAnnotations | object | `{}` |  |
| controller.loadBalancerSourceRanges[0] | string | `"0.0.0.0/0"` |  |
| controller.extraPorts | list | `[]` |  |
| controller.installPlugins[0] | string | `"kubernetes:3734.v562b_b_a_627ea_c"` |  |
| controller.installPlugins[1] | string | `"workflow-aggregator:590.v6a_d052e5a_a_b_5"` |  |
| controller.installPlugins[2] | string | `"git:4.13.0"` |  |
| controller.installPlugins[3] | string | `"configuration-as-code:1569.vb_72405b_80249"` |  |
| controller.installLatestPlugins | bool | `true` |  |
| controller.installLatestSpecifiedPlugins | bool | `false` |  |
| controller.additionalPlugins | list | `[]` |  |
| controller.initializeOnce | bool | `false` |  |
| controller.overwritePluginsFromImage | bool | `true` |  |
| controller.projectNamingStrategy | string | `"standard"` |  |
| controller.enableRawHtmlMarkupFormatter | bool | `false` |  |
| controller.scriptApproval | list | `[]` |  |
| controller.initScripts | list | `[]` |  |
| controller.existingSecret | string | `nil` |  |
| controller.additionalExistingSecrets | list | `[]` |  |
| controller.additionalSecrets | list | `[]` |  |
| controller.secretClaims | list | `[]` |  |
| controller.cloudName | string | `"kubernetes"` |  |
| controller.JCasC.defaultConfig | bool | `true` |  |
| controller.JCasC.configUrls | list | `[]` |  |
| controller.JCasC.configScripts | object | `{}` |  |
| controller.JCasC.security.apiToken.creationOfLegacyTokenEnabled | bool | `false` |  |
| controller.JCasC.security.apiToken.tokenGenerationOnCreationEnabled | bool | `false` |  |
| controller.JCasC.security.apiToken.usageStatisticsEnabled | bool | `true` |  |
| controller.JCasC.securityRealm | string | `"local:\n  allowsSignup: false\n  enableCaptcha: false\n  users:\n  - id: \"${chart-admin-username}\"\n    name: \"Jenkins Admin\"\n    password: \"${chart-admin-password}\""` |  |
| controller.JCasC.authorizationStrategy | string | `"loggedInUsersCanDoAnything:\n  allowAnonymousRead: false"` |  |
| controller.customInitContainers | list | `[]` |  |
| controller.sidecars.configAutoReload.enabled | bool | `true` |  |
| controller.sidecars.configAutoReload.image | string | `"registry1.dso.mil/ironbank/kiwigrid/k8s-sidecar:1.22.3"` |  |
| controller.sidecars.configAutoReload.imagePullPolicy | string | `"IfNotPresent"` |  |
| controller.sidecars.configAutoReload.resources.limits.cpu | string | `"100m"` |  |
| controller.sidecars.configAutoReload.resources.limits.memory | string | `"100Mi"` |  |
| controller.sidecars.configAutoReload.resources.requests.cpu | string | `"100m"` |  |
| controller.sidecars.configAutoReload.resources.requests.memory | string | `"100Mi"` |  |
| controller.sidecars.configAutoReload.reqRetryConnect | int | `10` |  |
| controller.sidecars.configAutoReload.sshTcpPort | int | `1044` |  |
| controller.sidecars.configAutoReload.folder | string | `"/var/jenkins_home/casc_configs"` |  |
| controller.sidecars.configAutoReload.containerSecurityContext.readOnlyRootFilesystem | bool | `true` |  |
| controller.sidecars.configAutoReload.containerSecurityContext.allowPrivilegeEscalation | bool | `false` |  |
| controller.sidecars.other | list | `[]` |  |
| controller.schedulerName | string | `""` |  |
| controller.nodeSelector | object | `{}` |  |
| controller.terminationGracePeriodSeconds | string | `nil` |  |
| controller.terminationMessagePath | string | `nil` |  |
| controller.terminationMessagePolicy | string | `nil` |  |
| controller.tolerations | list | `[]` |  |
| controller.affinity | object | `{}` |  |
| controller.priorityClassName | string | `nil` |  |
| controller.podAnnotations | object | `{}` |  |
| controller.statefulSetAnnotations | object | `{}` |  |
| controller.updateStrategy | object | `{}` |  |
| controller.ingress.enabled | bool | `false` |  |
| controller.ingress.paths | list | `[]` |  |
| controller.ingress.apiVersion | string | `"extensions/v1beta1"` |  |
| controller.ingress.labels | object | `{}` |  |
| controller.ingress.annotations | object | `{}` |  |
| controller.ingress.hostName | string | `nil` |  |
| controller.ingress.tls | string | `nil` |  |
| controller.secondaryingress.enabled | bool | `false` |  |
| controller.secondaryingress.paths | list | `[]` |  |
| controller.secondaryingress.apiVersion | string | `"extensions/v1beta1"` |  |
| controller.secondaryingress.labels | object | `{}` |  |
| controller.secondaryingress.annotations | object | `{}` |  |
| controller.secondaryingress.hostName | string | `nil` |  |
| controller.secondaryingress.tls | string | `nil` |  |
| controller.backendconfig.enabled | bool | `false` |  |
| controller.backendconfig.apiVersion | string | `"extensions/v1beta1"` |  |
| controller.backendconfig.name | string | `nil` |  |
| controller.backendconfig.labels | object | `{}` |  |
| controller.backendconfig.annotations | object | `{}` |  |
| controller.backendconfig.spec | object | `{}` |  |
| controller.route.enabled | bool | `false` |  |
| controller.route.labels | object | `{}` |  |
| controller.route.annotations | object | `{}` |  |
| controller.hostAliases | list | `[]` |  |
| controller.prometheus.enabled | bool | `false` |  |
| controller.prometheus.serviceMonitorAdditionalLabels | object | `{}` |  |
| controller.prometheus.scrapeInterval | string | `"60s"` |  |
| controller.prometheus.scrapeEndpoint | string | `"/prometheus"` |  |
| controller.prometheus.alertingRulesAdditionalLabels | object | `{}` |  |
| controller.prometheus.alertingrules | list | `[]` |  |
| controller.prometheus.prometheusRuleNamespace | string | `""` |  |
| controller.prometheus.relabelings | list | `[]` |  |
| controller.prometheus.metricRelabelings | list | `[]` |  |
| controller.googlePodMonitor.enabled | bool | `false` |  |
| controller.googlePodMonitor.scrapeInterval | string | `"60s"` |  |
| controller.googlePodMonitor.scrapeEndpoint | string | `"/prometheus"` |  |
| controller.testEnabled | bool | `true` |  |
| controller.httpsKeyStore.jenkinsHttpsJksSecretName | string | `""` |  |
| controller.httpsKeyStore.enable | bool | `false` |  |
| controller.httpsKeyStore.httpPort | int | `8081` |  |
| controller.httpsKeyStore.path | string | `"/var/jenkins_keystore"` |  |
| controller.httpsKeyStore.fileName | string | `"keystore.jks"` |  |
| controller.httpsKeyStore.password | string | `"password"` |  |
| controller.httpsKeyStore.jenkinsKeyStoreBase64Encoded | string | `"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\n"` |  |
| agent.enabled | bool | `true` |  |
| agent.defaultsProviderTemplate | string | `""` |  |
| agent.jenkinsUrl | string | `nil` |  |
| agent.jenkinsTunnel | string | `nil` |  |
| agent.kubernetesConnectTimeout | int | `5` |  |
| agent.kubernetesReadTimeout | int | `15` |  |
| agent.maxRequestsPerHostStr | string | `"32"` |  |
| agent.namespace | string | `nil` |  |
| agent.image | string | `"registry1.dso.mil/ironbank/opensource/jenkins/inbound-agent"` |  |
| agent.tag | string | `"3085.vc4c6977c075a-4"` |  |
| agent.workingDir | string | `"/home/jenkins/agent"` |  |
| agent.nodeUsageMode | string | `"NORMAL"` |  |
| agent.customJenkinsLabels | list | `[]` |  |
| agent.imagePullSecretName | string | `"private-registry"` |  |
| agent.componentName | string | `"jenkins-agent"` |  |
| agent.websocket | bool | `false` |  |
| agent.privileged | bool | `false` |  |
| agent.runAsUser | string | `nil` |  |
| agent.runAsGroup | string | `nil` |  |
| agent.hostNetworking | bool | `false` |  |
| agent.resources.requests.cpu | string | `"512m"` |  |
| agent.resources.requests.memory | string | `"512Mi"` |  |
| agent.resources.limits.cpu | string | `"512m"` |  |
| agent.resources.limits.memory | string | `"512Mi"` |  |
| agent.alwaysPullImage | bool | `false` |  |
| agent.podRetention | string | `"Never"` |  |
| agent.showRawYaml | bool | `true` |  |
| agent.volumes | list | `[]` |  |
| agent.workspaceVolume | object | `{}` |  |
| agent.envVars | list | `[]` |  |
| agent.secretEnvVars | list | `[]` |  |
| agent.nodeSelector | object | `{}` |  |
| agent.command | string | `nil` |  |
| agent.args | string | `"${computer.jnlpmac} ${computer.name}"` |  |
| agent.sideContainerName | string | `"jnlp"` |  |
| agent.TTYEnabled | bool | `false` |  |
| agent.containerCap | int | `10` |  |
| agent.podName | string | `"default"` |  |
| agent.idleMinutes | int | `0` |  |
| agent.yamlTemplate | string | `""` |  |
| agent.yamlMergeStrategy | string | `"override"` |  |
| agent.connectTimeout | int | `100` |  |
| agent.annotations | object | `{}` |  |
| agent.additionalContainers | list | `[]` |  |
| agent.disableDefaultAgent | bool | `false` |  |
| agent.podTemplates | object | `{}` |  |
| additionalAgents | object | `{}` |  |
| persistence.enabled | bool | `true` |  |
| persistence.existingClaim | string | `nil` |  |
| persistence.storageClass | string | `nil` |  |
| persistence.annotations | object | `{}` |  |
| persistence.labels | object | `{}` |  |
| persistence.accessMode | string | `"ReadWriteOnce"` |  |
| persistence.size | string | `"8Gi"` |  |
| persistence.volumes | string | `nil` |  |
| persistence.mounts | string | `nil` |  |
| networkPolicy.enabled | bool | `false` |  |
| networkPolicy.apiVersion | string | `"networking.k8s.io/v1"` |  |
| networkPolicy.internalAgents.allowed | bool | `true` |  |
| networkPolicy.internalAgents.podLabels | object | `{}` |  |
| networkPolicy.internalAgents.namespaceLabels | object | `{}` |  |
| networkPolicy.externalAgents | object | `{}` |  |
| rbac.create | bool | `true` |  |
| rbac.readSecrets | bool | `false` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `nil` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.imagePullSecretName | string | `nil` |  |
| serviceAccountAgent.create | bool | `false` |  |
| serviceAccountAgent.name | string | `nil` |  |
| serviceAccountAgent.annotations | object | `{}` |  |
| serviceAccountAgent.imagePullSecretName | string | `nil` |  |
| backup.enabled | bool | `false` |  |
| backup.componentName | string | `"backup"` |  |
| backup.schedule | string | `"0 2 * * *"` |  |
| backup.labels | object | `{}` |  |
| backup.serviceAccount.create | bool | `true` |  |
| backup.serviceAccount.name | string | `nil` |  |
| backup.serviceAccount.annotations | object | `{}` |  |
| backup.activeDeadlineSeconds | string | `""` |  |
| backup.image.repository | string | `"maorfr/kube-tasks"` |  |
| backup.image.tag | string | `"0.2.0"` |  |
| backup.imagePullSecretName | string | `nil` |  |
| backup.extraArgs | list | `[]` |  |
| backup.existingSecret | object | `{}` |  |
| backup.env | list | `[]` |  |
| backup.resources.requests.memory | string | `"1Gi"` |  |
| backup.resources.requests.cpu | int | `1` |  |
| backup.resources.limits.memory | string | `"1Gi"` |  |
| backup.resources.limits.cpu | int | `1` |  |
| backup.destination | string | `"s3://jenkins-data/backup"` |  |
| backup.onlyJobs | bool | `false` |  |
| backup.usePodSecurityContext | bool | `true` |  |
| backup.runAsUser | int | `1000` |  |
| backup.fsGroup | int | `1000` |  |
| backup.securityContextCapabilities | object | `{}` |  |
| cronJob.apiVersion | string | `"batch/v1"` |  |
| checkDeprecation | bool | `true` |  |
| awsSecurityGroupPolicies.enabled | bool | `false` |  |
| awsSecurityGroupPolicies.policies[0].name | string | `""` |  |
| awsSecurityGroupPolicies.policies[0].securityGroupIds | list | `[]` |  |
| awsSecurityGroupPolicies.policies[0].podSelector | object | `{}` |  |
| domain | string | `"bigbang.dev"` |  |
| istio.enabled | bool | `false` |  |
| istio.mtls | object | `{"mode":"STRICT"}` | Default argocd peer authentication |
| istio.mtls.mode | string | `"STRICT"` | STRICT = Allow only mutual TLS traffic, PERMISSIVE = Allow both plain text and mutual TLS traffic |
| istio.jenkins.enabled | bool | `true` |  |
| istio.jenkins.annotations | object | `{}` |  |
| istio.jenkins.labels | object | `{}` |  |
| istio.jenkins.gateways[0] | string | `"istio-system/main"` |  |
| istio.jenkins.hosts[0] | string | `"jenkins.{{ .Values.domain }}"` |  |
| istio.injection | string | `"disabled"` |  |
| monitoring.enabled | bool | `false` |  |
| networkPolicies.enabled | bool | `false` |  |
| bbtests.enabled | bool | `false` |  |
| bbtests.cypress.envs.cypress_url | string | `"http://jenkins.svc.cluster.local:8080"` |  |
| bbtests.scripts.envs.URL | string | `"http://jenkins.svc.cluster.local:8080"` |  |

## Contributing

Please see the [contributing guide](./CONTRIBUTING.md) if you are interested in contributing.
