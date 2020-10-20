# Changelog

## v1.9.0-rc2

The summary of changes below reflect the diff between the last stable RC (v1.9.0-rc1) and tag v1.9.0-rc2.

Summary of Changes
------------------

**Minor Changes:**
* Add a new daemon CLI argument, "--iptables-random-fully" to specify the
 iptables "--random-fully" argument when invoking the iptables CLI binary
 directly from cilium-agent. (#13383, @kh34)
* Add an alternative method to generate the Hubble mTLS certificates based on Kubernetes Jobs. (#13449, @gandro)
* Azure IPAM: option to ignore primary addresses (#13415, @bpineau)
* cli: Add cilium bpf lb maglev get $SVC_ID (#13586, @brb)
* Create healthz HTTP endpoint for kube-proxy replacement (#11733, @soumynathan)
* Helm: support affinity settings for operator (#13548, @youssefazrak)
* maglev: Add native implementation of murmur3 (#13501, @brb)

**Bugfixes:**
* bpf: only clean up XDP from devices with XDP attached (#13532, @jaffcheng)
* cilium, ipsec: Do revalidate_data_pull() early in do_decrypt() case (#13500, @jrfastab)
* Fix 1 potential deadlock in Azure IPAM and 1 other in ENI and Azure IPAM (#13517, @aanm)
* Fix bug where events cannot be enqueued during endpoint restoration (#13608, @christarazi)
* Fix natting of non-first ipv4 fragments. (#13476, @liuyuan10)
* Fixes panic when setting up encryption with azure IPAM (#13593, @aanm)
* identity: Fix nil pointer panic in LookupIdentityByID (#13514, @gandro)
* Ignore "Failed to load program" errors when Cilium agent is being teared down (#13281, @mrostecki)
* kvstore: Do not write to read-only keys in join-cluster mode (#13524, @jrajahalme)
* loader: Check if device has BPF prog before trying to detach it (#13591, @pchaigno)
* lock: fix data race in (*SemaphoredMutexSuite).TestParallelism() (#13570, @tklauser)
* service: Use initNextID in acquireLocalID() (#13576, @hzhou8)

**CI Changes:**
* build: Fix CC for CGO compilation for Arm (#13605, @errordeveloper)
* images: Fix handling of git tags (#13602, @errordeveloper)
* test: Fix kube-proxy-free on GKE due to wrong k8sServiceHost value (#13559, @pchaigno)
* test: Increase timeout for waiting LB IP addr on GKE (#13557, @brb)
* update cilium and hubble-relay dockerfiles to use built-in buildx ARGs (#13551, @xUnholy)

**Misc Changes:**
* allocator/podcidr: fix race conditions in tests (#13567, @aanm)
* api-limiter: Make auto adjust test less flaky (#13568, @twpayne)
* Avoid loops with local-redirect service translation (#13287, @aditighag)
* bpf_host: describe the position of {to,from}-{host,netdev} in the data path (#13483, @ti-mo)
* build Add a debug make target (#13522, @aditighag)
* ci: Do not label control plane nodes with cilium.io/node (#13504, @mrostecki)
* Cilium Agent will now wait for CRDs to become available instead of the Operator; the Operator will register the CRDs (#13418, @christarazi)
* CODEOWNERS: change docs to docs-structure (#13589, @aanm)
* CODEOWNERS: fix owner assignment for hubble related helm charts (#13540, @Rolinh)
* Disable bandwidth-manager by default for new deployments (#13515, @qmonnet)
* doc: Kubeadm guide (#13488, @mrostecki)
* docs/performance: update scripts repo and tf version (#13596, @kkourt)
* docs: Add Hubble to SIGs table (#13563, @b3a-dev)
* docs: Adjust the hubble CLI definition (#13546, @glibsm)
* docs: Fix shell syntax issue in OpenShift guide (#13560, @errordeveloper)
* docs: Update CI documentation following Helm refactoring (#13561, @pchaigno)
* Fix extraction of manifest for OpenShift (#13598, @errordeveloper)
* Fix install/kubernetes update-versions make target (#13523, @joestringer)
* Fix kubectl command in cassandra NetworkPolicy documentation. (#13545, @velp)
* Fix typo in UpdateEC2AdapterLimitViaAPI command line flag (#12969, @soumynathan)
* Fixes errors "executable file not found" in script examples/kubernetes-cassandra/cass-populate-tables.sh (#13534, @velp)
* fqdn: remove remnants godoc comments mentioning DNS poller (#13531, @tklauser)
* helm: bring back hubble dependencies validation (#13539, @Rolinh)
* helm: Correct indentation for imagePullSecret (#13547, @sayboras)
* helm: improve hubble related config documentation in values file (#13566, @Rolinh)
* helm: remove random value file (#13538, @Rolinh)
* helm: Remove unused serviceAccount values (#13585, @gandro)
* helm: remove unused var in make quick-install target (#13541, @Rolinh)
* helm: Update documentation links to point to stable (#13520, @joestringer)
* helm: Update README.md for helm chart (#13584, @sayboras)
* Improve policy documentation (#13409, @manuelbuil)
* install/kubernetes: consistent case spelling of iptables related values (#13556, @tklauser)
* install: repository changed from quay.io to docker.io for hubble-ui (#13542, @yandzee)
* maps: move mocks into separate testutils/mockmaps package (#13489, @jibi)
* pkg/azure/ipam: fix data race in (*Node).PopulateStatusFields (#13581, @tklauser)
* pkg/hubble: ignore klog/v2 in goleak detector (#13525, @aanm)
* pkg/idpool: fix test for race detector (#13562, @aanm)
* pkg/k8s: mark unused 'k8s-watcher-queue-size' flag for removal (#13536, @aanm)
* pkg/policy: ignore test mutex comparison (#13582, @aanm)
* Prepare v1.9.0-rc2 release (#13618, @aanm)
* Revert "Differentiate UDP and TCP Protocols in Services" (#13587, @nathanjsweet)
* test/vagrant: Fix NFS setup for test VMs (#13527, @pchaigno)
* test: Disable host firewall by default when running tests locally (#13465, @pchaigno)
* Update Go to 1.15.3 (#13578, @tklauser)
* vagrant: Default to NFS in the dev. VMs (#13516, @pchaigno)
* vagrant: New kubectl aliases (#13470, @pchaigno)

## v1.9.0-rc1

The summary of changes below reflect the diff between the last stable release (v1.8.4) and tag v1.9.0-rc1.

Summary of Changes
------------------

**Major Changes:**
* Add deny policies (#12716, @aanm)
* Add Maglev consistent hashing to kube-proxy replacement for NodePort/LoadBalancer/externalIPs services (#13131, @brb)
* Add support for k8s 1.19 (#12611, @aanm)
* Added support for non-k8s nodes to register to a k8s cluster via new option `--join-cluster` (#13309, @jrajahalme)
* Add experimental multi-platform images (#12013, @errordeveloper)
* Add bandwidth manager (#12868, @borkmann)
* Direct routing performance improvement through new tc/BPF-only based host forwarding mode w/o passing to upper stack. (#13330, @borkmann)
* Overhaul of Helm chart structure to simplify & improve upgrades (#13259, @seanmwinn)
* Implement eBPF native local service redirect functionality (#12831, @aditighag)
* Implement proxy redirection logic in eBPF (#11279, @joestringer)

**Minor Changes:**
* Add blacklistConflictingRoutes parameter to config chart (#11368, @donch)
* Add a `node` label to agent metrics. (#12965, @diversario)
* Add automatic generation of CRDs for CNP and CCNP (#11607, @christarazi)
* Add BPF map sizes to output of `cilium status --verbose` (#12660, @tklauser)
* add CLI for checking kernel capabilities (#11339, @brandshaide)
* Add config point to send bugtool to stdout (#12837, @willdeuschle)
* Add configurable enable-k8s-endpoint-slice (#13029, @Antiarchitect)
* Add detection of unknown fields for policies (CNP & CCNP) in preflight (#13180, @christarazi)
* add hint to make use of CLI cilium kernel-check in system requirements (#13164, @brandshaide)
* api/v1: Add ability to query flows by HTTP method (#13328, @glibsm)
* api/v1: Add drop_reason_desc enum to Flow API (#13301, @kAworu)
* Automate generation of CiliumNode, CiliumIdentity, & CiliumEndpoint CRDs using controller-gen (#11476, @aanm)
* Azure IPAM: don't install bogus "PodCIDR via cilium_host" route by default (#13098, @bpineau)
* build: Skip 'clean' and 'clean-container' before docker image builds. (#12463, @jrajahalme)
* cilium/build Add GOPATH check for generate-k8s-api (#12695, @aditighag)
* cleanup/ipam: Remove hostscope-legacy IPAM option (#12984, @sayboras)
* cmd: Allow to filter metrics with regexp (#12590, @mrostecki)
* Differentiate load-balancer keys in the datapath by protocol (in addition to address and port), so that cilium can correctly differentiate protocols between services. (#12628, @nathanjsweet)
* Enable host firewall without remote-node identity (#12878, @pchaigno)
* Enable support for user managed identities in the `cilium-operator` (#12592, @ungureanuvladvictor)
* Envoy metrics from the Cilium host proxy are exported via a prometheus port. (#12949, @jrajahalme)
* envoy: Add development support for Envoy filter metadata enforcement (#12500, @jrajahalme)
* envoy: Move to Envoy API v3 (#12331, @jrajahalme)
* envoy: Optimize list of allowed remote security IDs (#12926, @jrajahalme)
* envoy: Stop using deprecated filter names (#13351, @jrajahalme)
* envoy: Update to release 1.14.4 (#12484, @jrajahalme)
* Fail to start if IPSec and devices are used together (#13069, @tobiaskohlbau)
* Fix typo in AKS getting started guide (#12505, @ap4y)
* fix(3891): mirror parent pod labels to cilium endpoints (#12406, @fristonio)
* fix(9966): fix creation of multiple KVStore watchers for CNPs and CCNPs (#12323, @fristonio)
* Follow-up for `cilium ip list` identity lookup (#13375, @tklauser)
* helm: allow setting conntrack-gc-interval in cilium-config cm (#13061, @ghouscht)
* helm: bump hubble-ui patch version in chart values (#13313, @genbit)
* helm: configurable annotations for agent and operator pods (#12189, @mvisonneau)
* hubble-relay: add support for (m)TLS (#12900, @Rolinh)
* hubble/metrics: Add protocol labels to `flows_processed_total` (#12742, @sayboras)
* hubble: add support for (m)TLS (#12906, @Rolinh)
* hubble: Add support for PERF_RECORD_LOST (#12475, @gandro)
* Kafka proxy is now implemented in Cilium Go extensions for Envoy, which adds egress policy enforcement support for Kafka L7 policies. (#12548, @jrajahalme)
* lbmap: Sort backends before creating maglev lookup table (#13461, @brb)
* maglev: Perf related follow up items (#13431, @brb)
* Make pods IPv6 address discoverable on node's subnet (#12193, @anfernee)
* Makes k8sNodeIP the preferred IP when initializing NodePort addresses. (#13223, @networkop)
* metrics: Deprecate non-conventional prometheus metrics (#12826, @sayboras)
* monitor: Add option to disable monitor independently of Hubble (#12540, @gandro)
* operator: Remove options deprecated in v1.8 (#12676, @pchaigno)
* pkg/hubble/filters: Add HTTP path filters (#13425, @twpayne)
* pkg/option: add option to configure BPF lbmap size (#12843, @fristonio)
* policy/trace: Support recent api versions for {Deployment, ReplicaSet} (#12903, @sayboras)
* Remove "blacklist-conflicting-routes" option from cilium-agent. (#12986, @fristonio)
* Remove agent options deprecated in v1.8 (#12642, @tklauser)
* Remove deprecated `cilium bpf proxy` commands (#12682, @tklauser)
* Remove DNS poller after being deprecated in Cilium 1.8. (#13229, @tklauser)
* Remove PodSecurityPolicy in helm due to deprecation and future removal in Kubernetes (#12469, @sayboras)
* Removed helm 2 support. Move requirements.yaml to Chart.yaml and set min. helm version to helm 3 (#12412, @sayboras)
* Rename IPAM API metrics to be `ec2` specific. (#12502, @ungureanuvladvictor)
* Show names for reserved identities in `cilium ip list`. (#13304, @tklauser)
* The metrics `endpoint_regeneration_time_stats` and `policy_regeneration_time_stats` had their 'buildTime' scopes renamed to 'total'. (#13323, @ti-mo)
* TLS certificates hot reloading for Hubble and Relay (#13249, @kAworu)
* Update Kubernetes dependencies to v1.19.1 and etcd to 3.4.13 (#13134, @aanm)
* Update Kubernetes libraries to 1.19.2 (#13199, @aanm)
* Upgrade CRDs (apiextensions) from v1beta1 to v1 (#11477, @aanm)

**Bugfixes:**
* Add the `update-ec2-apdater-limit-via-api` flag to the `cilium-operator-aws`. (#12410, @ungureanuvladvictor)
* agent: fix panic when clustermesh not set and cluster-id is non-zero (#12944, @ArthurChiao)
* cilium: allow encryption/decryption to coexist with bpf_host logic (#13238, @jrfastab)
* Hubble-relay now proxies the GRPC context to its servers. (#12865, @nathanjsweet)
* Valid CNP and CCNP 'matchLabel' values must be 63 characters or less and must be empty or begin and end with an alphanumeric character ([a-z0-9A-Z]) with dashes (-), underscores (_), dots (.), and alphanumerics between. (#12117, @aanm)
* Various other bugfixes already included in v1.8.5 or earlier releases

**CI Changes:**
* .github, .travis: bump golangci-lint to 1.31 (#13245, @tklauser)
* Add portmap+proxy conformance test (#12758, @joestringer)
* build: Fix shellcheck errors (#12407, @errordeveloper)
* build: Fix shellcheck linter (#12432, @errordeveloper)
* build: Simplify how `BPF_SRCFILES` is set in git-free mode (#12326, @errordeveloper)
* build: Update runtime image, add a guard rail (#12435, @errordeveloper)
* ci/gke: Fix Hubble Relay on GKE (#13025, @gandro)
* ci: add DeleteLong to accommodate longer resource deletion (#12743, @nebril)
* ci: add startup-script to local node repo (#12359, @nebril)
* ci: Delete cilium-node-init ds before cilium install (#12725, @nebril)
* ci: fix runtime kernel version typo (#13255, @nebril)
* ci: lock docker build (#13258, @nebril)
* ci: lower ginkgo timeout (#12570, @nebril)
* ci: pass race-detection env vars to vagrant boxes (#13253, @nebril)
* ci: refactor curl / wget test helpers with retries (#12408, @JieJhih)
* ci: release gke nodepool (#12382, @nebril)
* ci: Retry gke cluster scaling (#12616, @nebril)
* ci: Run policy stress tests on a nightly basis (#13306, @nebril)
* ci: Start separate registries for gke builds (#12782, @nebril)
* Fix overall races in the Cilium code base (#12789, @aanm)
* Fix typo in gke cluster release script (#12681, @nebril)
* Fix upgrade testing for v1.9-dev (#12309, @aanm)
* Fixes LRP service deletion/restoration and adds e2e tests for LRP. (#13360, @Weil0ng)
* images/cilium-test: New test suite image (#12941, @errordeveloper)
* Run ci with race detection (#13215, @nebril)
* Set GOPATH in CI VM (#12717, @aditighag)
* Smoke test with k8s 1.19 (#13021, @sayboras)
* smoke-test: Additional logs in case of error (#13017, @pchaigno)
* smoke-test: Print pod/deploy state on failure (#12689, @joestringer)
* test, images: update helm to 3.3.4 (#13277, @tklauser)
* test/helpers: dump rbac information on k8s test failure (#12866, @fristonio)
* test/Vagrantfile: disable unattended-upgrades (#11826, @qmonnet)
* test: add missing artii cert-key pair (#12303, @nebril)
* test: Add nightly policy stress test (#12933, @jrajahalme)
* test: add services conformance test to kubernetes upstream suite (#13176, @fristonio)
* test: auto correct grafana port in test vagrant vms (#13202, @nebril)
* test: bump latest helm chart version (#12093, @aanm)
* test: bump stable version to 1.8 (#12094, @aanm)
* test: check logs of operator and hubble relay (#13266, @nebril)
* test: don't check logs if kubectl is nil (#13389, @nebril)
* test: enable operator metrics in stresspolicy suite (#13343, @nebril)
* test: fix build after merge of #13107 and #13036 (#13124, @tklauser)
* test: fix cilium policy action for clusterwide policies (#13464, @fristonio)
* test: fixed failing missed k8s tests (#12887, @fristonio)
* test: gather init container logs (#12762, @nebril)
* test: Improve logging of errors that must be investigated (#12598, @joestringer)
* test: Increase range of accepted values for bandwidth test (#13103, @pchaigno)
* test: make it possible to pass PROVISION when running tests via make (#12253, @Rolinh)
* test: put hubble tests on quarantine in GKE (#12746, @nebril)
* test: Restart unmanaged pods in log gatherer ns (#13413, @nebril)
* test: Simplify Cilium namespace handling (#13107, @pchaigno)
* test: Test NodePort BPF with L7 proxy (#12434, @brb)
* test: Try out all GKE clusters in random order (#12661, @jrajahalme)
* test: Update coredns image tag from 1.2.2 to 1.2.6 for k8s 1.12 (#12869, @jrajahalme)
* test: update k8s test versions to 1.16.14, 1.17.11 and 1.18.8 (#12880, @aanm)
* test: update runtime test descriptions after removal of DNS poller (#13391, @tklauser)
* test: Use `--no-cache` docker flag in gke builds (#12765, @nebril)
* test: use correct test image in nightlies, restart pods in gke tests (#13322, @nebril)
* Testing in DualStack K8s environment (#13288, @fristonio)
* travis: enable vm jobs of aarch64 (#13033, @Jianlin-lv)
* updating operator dockerfile with built-in buildx ARGs (#13462, @xUnholy)
* Use Docker buildkit in the CI (#12112, @jrajahalme)

**Misc Changes:**
* .gitattributes: Mark cmdref files as generated (#12960, @pchaigno)
* .github/cilium-actions: remove github action helper message (#12300, @aanm)
* .github: Bump projects after v1.8.0 release (#12266, @joestringer)
* .github: run Go prechecks as GitHub action (#12693, @tklauser)
* .github: set kind/bug label in bug issue template (#12872, @tklauser)
* .github: Update issue template (#12131, @errordeveloper)
* .github: Update issue template for flakes (#12797, @pchaigno)
* .gitignore: Ignore test/cilium.conf.ginkgo (#12133, @pchaigno)
* .travis: Fix probes_test failure on Arm64 (#12335, @Jianlin-lv)
* Add finleap connect as cilium user (#12792, @christianhuening)
* add Interface index to the CNI result (#12706, @mazzy89)
* Add missing Node annotations in documentation (#12575, @dabcoder)
* Add ND responder on native NIC to make endpoint IPv6 address discoverable on node network. (#12086, @anfernee)
* add_vagrant_box.sh: fix and document the script (#12264, @qmonnet)
* Address code tidiness items for bpf tproxy (#13050, @joestringer)
* allocator/podcidr: fix formatting issue with debug message (#13447, @aanm)
* api/v1: Compile hubble proto in docker (#12931, @glibsm)
* api/v1: Include Makefile in the hubble proto image (#13147, @glibsm)
* api/v1: update swagger to 0.25.0 (#12673, @aanm)
* api: do not require grpc service implementations to embed stubs (#12808, @Rolinh)
* api: re-generate protobuf code (#12677, @Rolinh)
* bpf, cocci: small follow-ups (#12962, @borkmann)
* bpf: clean up .PHONY targets for Makefiles (#13142, @qmonnet)
* bpf: configure mtu for the created $ENCAP_DEV (#12972, @Jianlin-lv)
* bpf: Do not try to open map when creating unpinned map (#13427, @brb)
* bpf: minor fix to Makefile and includes (#12819, @qmonnet)
* bpf: remove dead stores in tail_nodeport_nat_ipv{4,6} (#12334, @tklauser)
* bpf: Remove duplicate command from init.sh (#13468, @pchaigno)
* build: Opt-in for docker build commit requirement (#12365, @jrajahalme)
* build: Stabilize bpf file sort order. (#12464, @jrajahalme)
* bump Alpine base image to 3.12 (#13403, @Rolinh)
* Bump aws/aws-sdk-go-v2 to 0.23.0 from 0.18.0 (#12393, @ungureanuvladvictor)
* Bump readme for v1.8.0 release (#12227, @joestringer)
* chore(ci): Correct indentation for github action workflows (#12828, @sayboras)
* chore(lint): To enable linter for test files (#12402, @sayboras)
* chore(misspell): To enable misspell linter for go codes (#12490, @sayboras)
* Cilium Operator will now handle CRD operations on behalf of Cilium Agent (#13285, @christarazi)
* cilium/cmd: remove deprecated rev flag used with `cilium service update` (#12692, @tklauser)
* cilium: bandwidth manager e2e tests (#12961, @borkmann)
* cilium: enable more ci tests for bw manager (#13030, @borkmann)
* cilium: make bandwidth manager dependent on 5.1+ (#13117, @borkmann)
* cleanup: remove unused code (#13381, @florianl)
* cleanup: Use value receiver instead of pointer receiver for CIDR (#12563, @sayboras)
* clustermesh_doc: Adding shared service doc in clustermesh (#13145, @chowmean)
* cocci: Fix false positive in null.cocci (#12422, @pchaigno)
* CODEOWNERS: Add contrib/ (#12641, @pchaigno)
* CODEOWNERS: add hubble as codeowner for hubble related helm charts (#12431, @Rolinh)
* CODEOWNERS: Include .github directory (#12135, @pchaigno)
* CODEOWNERS: Update Kubernetes owners (#12883, @christarazi)
* common: remove unused func FindEPConfigCHeader (#12425, @tklauser)
* connectivity-check: Check cue file formatting in Github Action (#13088, @sayboras)
* connectivity-check: Fix YAML inconsistency (#13073, @joestringer)
* connectivity-check: Fix YAML inconsistency (#13075, @sayboras)
* contrib/checkpr.sh: fix job name (#12236, @qmonnet)
* contrib/vagrant: add hosts field in all generated certificates (#12802, @aanm)
* contrib/vagrant: Allow to start a single VM (#12591, @mrostecki)
* contrib: extend checkpr.sh to watch for Smoke Tests completion (#12058, @qmonnet)
* contrib: provision cilium-operator before cilium (#13157, @aanm)
* contrib: Use fixed string search in grep (#12634, @christarazi)
* Correct help string for kubernetes_events_received_total metric (#12316, @ungureanuvladvictor)
* daemon: Disable bandwidth manager if IPSec is enabled (#13105, @pchaigno)
* datapath/connector: remove unused funcs (#13374, @tklauser)
* datapath/linux/probes: make ErrKernelConfigNotFound a sentinel error value (#12339, @tklauser)
* datapath/linux/route: use upstream function to list rules (#13380, @florianl)
* datapath/linux: document methods that must be called with mutex held (#12472, @tklauser)
* datapath/maps: drop cilium_policy_reserved_* maps from to-be-removed maps (#13151, @tklauser)
* datapath: change log level to info if kernel config is not available (#10317, @fristonio)
* doc: add concepts/observability section, document Hubble in cluster mesh (#13307, @Rolinh)
* doc: Add workarounds section to e2e testing guide (#12520, @christarazi)
* doc: correct operation command of manual installation (#12022, @Jianlin-lv)
* doc: document how to use custom TLS certificates with Hubble (#13291, @Rolinh)
* doc: Handle READTHEDOCS_VERSION in preview (#12158, @michi-covalent)
* doc: Rename BPF to eBPF (#12836, @tgraf)
* doc: Update AUTHORS file (#12142, @tgraf)
* doc: Update AUTHORS file (#13106, @kAworu)
* docker: Generate .dockerignore for BUILDKIT (#12375, @jrajahalme)
* docker: Update hubble image (#12608, @glibsm)
* docs(dev): Update the step for basic formating/lint checks (#12617, @sayboras)
* docs(e2e): Update kube version in e2e docs (#12769, @sayboras)
* docs(operator): Update coredns plugin from proxy to forward (#12578, @sayboras)
* docs: add command to run focused k8s bandwidth tests in CI (#13022, @fristonio)
* docs: Add connectivity-check to Hubble getting started guide (#13423, @twpayne)
* docs: Add link to CI failure triage to contributing guide (#13463, @twpayne)
* docs: Add note for users upgrading K8s (#13273, @christarazi)
* docs: Add SmileDirectClub to Cilium users (#12738, @particledecay)
* docs: clarify janitor duty for backport PRs (#11988, @aanm)
* docs: Clarify when GITHUB_TOKEN is needed (#13407, @pchaigno)
* docs: Document make target for operator Docker image (#13385, @pchaigno)
* docs: Document new Vagrant start.sh argument (#12601, @pchaigno)
* docs: Document RTD step for old branch on release (#12519, @joestringer)
* docs: Fix build (#13059, @joestringer)
* docs: fix rst table formatting in for stable releases (#12397, @borkmann)
* docs: Fix TLS visibility GSG (#13452, @jrajahalme)
* docs: fix typo (#12684, @kkourt)
* docs: Fix typo in add_vagrant_box path (#12421, @pchaigno)
* docs: Janitors should update backport PR labels (#12644, @pchaigno)
* docs: mention install/upgrade.rst in contrib guide (#13345, @ti-mo)
* docs: Remove "Experimental" from GKE E2E test section (#13426, @pchaigno)
* docs: update container image dependencies and distribution process (#11853, @aanm)
* docs: Update contributing docs (#13437, @twpayne)
* Enable doc building for arm64 in the Makefile (#12506, @TrevorTaoARM)
* Enable lint check as part of github action (#11528, @sayboras)
* Enable quick and experimential installation in CI (#12232, @sayboras)
* endpoint: Clean up the bwmap on pod termination (#12970, @pchaigno)
* Ensure that the socket is removed when api.SetDefaultPermissions fail (#12691, @kAworu)
* envoy: Avoid logger pointer data race (#12793, @jrajahalme)
* envoy: don't use deprecated listener and HTTP filter names (#13235, @tklauser)
* examples: Update host policy examples (#12959, @pchaigno)
* feat(configmap): Add support for setting labels in config map (#12646, @sayboras)
* feat(helm): Add serviceAccount field for hubble-ui (#12670, @sayboras)
* Fix bug in EKS environments where Cilium agents never become ready due to the CiliumNode CRD disallowing updates (#13195, @christarazi)
* Fix controller-tools module (#13055, @christarazi)
* Fix GetFlows Test (#13206, @nathanjsweet)
* Fix race condition in DeepEqual function (#13472, @aanm)
* Fix render-docs build again (#13158, @joestringer)
* Fix some word errors in the annotations (#12414, @TrevorTaoARM)
* Fix Spelling Errors for endpoint pkg (#12394, @TrevorTaoARM)
* fix: fix missing arguments declaration funcs in pkg/node/address_darwin (#13481, @genbit)
* Fixes printk. (#12610, @Weil0ng)
* Follow-up fixes for the API rate limiter (#13450, @tgraf)
* fqdn: remove unused fields and funcs after DNS poller removal (#13242, @tklauser)
* fqdn: remove unused test helper funcs (#13113, @tklauser)
* gitattributes: add examples/crds/*.yaml as linguist-generated (#12840, @aanm)
* github-workflow: Reduce scope of quick-install test (#13078, @tgraf)
* Give Hubble access to StoreGetter and include ContainerStatuses field for Pod (#12240, @michi-covalent)
* golangci: Enable varcheck linter (#11554, @mrostecki)
* health/server: drop dependency on github.com/c9s/goprocinfo (#12798, @tklauser)
* helm: remove hubble-ca-certs secret (#13290, @Rolinh)
* hubble, monitor: handle accesslog.DNSSourceProxy in log record parsers (#13114, @tklauser)
* hubble-relay: add support for LOCKDEBUG (#12320, @Rolinh)
* hubble/parser: Fix data race in L7 parser (#13467, @gandro)
* hubble/peer: always generate tls ServerName at the same DNS domain level (#13118, @kAworu)
* hubble/relay: compose ClientConn interface with grpc.ClientConnInterface (#12705, @Rolinh)
* hubble/relay: fix warning about missing config file (#13110, @kAworu)
* hubble: Add new monitor consumer implementation (#12711, @gandro)
* hubble: Switch GetEventsChannel to new consumer interface (#12712, @gandro)
* image/hubble-proto: Install bash in builder image (#13046, @gandro)
* images/builder: bump protoc to 3.12.4 (#12886, @tklauser)
* images/{Dockerfile.dockerignore}: do not ignore .git (#12915, @aanm)
* install/kubernetes: add disableEnvoyVersionCheck option (#12919, @aanm)
* install/kubernetes: quote disableEnvoyVersionCheck when option is set (#12922, @aanm)
* Invoke go-bindata from the vendor directory instead of requiring it explicitly (#12805, @christarazi)
* k8s: Disallow unknown fields in CNP & CCNP (#13382, @christarazi)
* k8s: Fix parsing of CCNPs (#12851, @pchaigno)
* k8s: Remove deprecated identity status field (#13053, @christarazi)
* k8s: test and add k8s 1.19.0 libraries (#13016, @aanm)
* k8s: update k8s to 1.19.0-rc.3 (#12708, @aanm)
* k8s: update k8s to 1.19.0-rc.4 (#12775, @aanm)
* loader: Refactor initArgMode assignments (#12238, @pchaigno)
* Lrp follow-up fixes (#13362, @aditighag)
* Misc: fix up spelling mistake (#12488, @Jianlin-lv)
* monitor: Add consumer interface for internal subscribers (#12710, @gandro)
* monitor: Avoid JSON-encoding agent events for in-memory storage (#12939, @gandro)
* monitor: Shorten policy-verdict output (#12137, @pchaigno)
* mountinfo speedups (#12249, @kolyshkin)
* Move single-use symbols out of pkg/common (#13368, @tklauser)
* operator: make: Add install target (#12204, @mrostecki)
* pkg/envoy: Fix Envoy MySQL test (#12790, @christarazi)
* pkg/k8s: fix race condition (#13471, @aanm)
* pkg/k8s: fix typo in unit tests due bad refactor (#12806, @aanm)
* pkg/k8s: remove manual generated DeepCopyInto function (#12680, @aanm)
* pkg/k8s: remove unused variable (#12696, @aanm)
* pkg/k8s: set schema version to 1.22.1 (#12921, @aanm)
* pkg/redirectpolicy Fix frontend-backend ipv6 mapping (#13494, @aditighag)
* policy language doc fix (#12404, @kAworu)
* policy: Do not dump selections on logs (#12927, @jrajahalme)
* policy: fix typo (#12364, @ArthurChiao)
* preflight: Use v1beta1 client when appropriate (#13312, @christarazi)
* preparing v1.9 dev cycle (#11781, @aanm)
* Prevent leak of AWS-related environment variables in `cilium-operator` deployment definition when deploying the operator in Azure mode. (#12411, @ungureanuvladvictor)
* proxy: remove unused dialer and socket code (#12744, @tklauser)
* README: Fix the versions listing (#13365, @joestringer)
* Reduce memory allocations during endpoint restore (#12405, @tklauser)
* release: Remove all unsused gitlib functions (#12259, @errordeveloper)
* Remove `ec2` notion from generic `cilium-operator` IPAM metrics. (#12413, @ungureanuvladvictor)
* Remove GitHub issue template for support request (#12957, @tgraf)
* Remove old proto dependencies (#13119, @glibsm)
* Rename azure-user-assigned-identity-name to azure-user-assigned-identity-id (#13390, @ungureanuvladvictor)
* replace Deployment with Job for example (#12455, @brandshaide)
* Replace use of github.com/pkg/errors and golang.org/x/xerrors with Go stdlib functionality (#12603, @tklauser)
* Restores ClusterIP service entry upon LRP removal. (#13274, @Weil0ng)
* Revise doc building to enable it on arm64 (#12231, @TrevorTaoARM)
* RFC: ip: Flesh out list of non-global scope prefixes (#11875, @joestringer)
* s/create/apply (#12987, @jimangel)
* smoke-test: Capture sysdump details for troubleshooting (#13090, @sayboras)
* Stop listening for Pod Container Status events, making Cilium's Kubernetes event watcher less resource consuming when a pod is deleted. (#13179, @aanm)
* style(errors.Is): To enforce errors.Is usage instead of comparison (#12707, @sayboras)
* style(imports): Remove duplicate imports in same file (#12747, @sayboras)
* test(github): Bump required protoc version to 3.12.3 (#12768, @sayboras)
* test(helm): Run smoke test in multi-node cluster (#11888, @sayboras)
* test(quick-install): Dump related logs and events for cilium, hubble and connectivity checks (#12286, @sayboras)
* test(smoketest): Set liveness and readiness timeout in connectivity check (#13067, @sayboras)
* test/conformance: Disable pulling latest image in ipv6 test (#13204, @sayboras)
* test/packet: extend add_vagrant_box.sh script to load dev/CI images (#11871, @qmonnet)
* test/packet: set operating_system to ubuntu_18_04 (#12476, @aanm)
* test: Add monitoring to the flaky FQDN test (#12061, @jrajahalme)
* test: enable hubble tls in ci (#13232, @kAworu)
* test: Fetch DNS proxy port from `ss -uap` (#12577, @joestringer)
* test: fix ipv6 addr configuration for vm interfaces (#13445, @fristonio)
* test: further increase range of accepted values for bandwidth test (#13372, @borkmann)
* test: properly clean up cilium components in ginkgo contexts (#12763, @fristonio)
* test: Quarantine flaky GuestBook test (#13000, @pchaigno)
* test: Quarantine K8sIstioTest while flaky (#13014, @pchaigno)
* test: Remove incorrect comment on flakyness (#12821, @pchaigno)
* test: Remove old `startup-script` image dir (#12340, @errordeveloper)
* test: Test for vxlan + per-endpoint routes (#13466, @pchaigno)
* test: Update docker image references (#12579, @pchaigno)
* test: Use smaller, updated docker images (#12583, @pchaigno)
* travis: remove Arm64 jobs from allow_failures (#13172, @Jianlin-lv)
* ui: updated helm charts for hubble-ui 0.7 (#13170, @geakstr)
* Update documentation for kubectl usage (#12487, @JieJhih)
* Update Go to 1.15.2 (#13139, @tklauser)
* Update MAINTAINERS file (#12200, @tgraf)
* Update protobuf and gRPC related dependencies (#12767, @Rolinh)
* Update self-managed k8s docs to exclude Azure IPAM link (based on AKS). (#12539, @ungureanuvladvictor)
* Update stable releases (#11938, #12047, #12392, #12635, #13089, #12780, #13363, #13013, #13045, @aanm, @christarazi, and @joestringer)
* Use existing consts for Cilium CRD names (#12928, @tklauser)
* Use net.JoinHostPort to construct network address strings (#12975, @tklauser)
* use os.user instead of reading /etc/group (#12638, @kAworu)
* Use right schema when validating CCNP in pre-flight upgrade step (#12106, @aanm)
* USERS: Add Alibaba Cloud usage (#13453, @tgraf)
* USERS: Add Google and DigitalOcean (#13108, @tgraf)
* USERS: Add microk8s (#13478, @tgraf)
* Vagrant overall improvements (#12477, @aanm)
* vagrant start script misc updates (#13444, @kkourt)
* vagrant: Bump all vagrant box versions (#12261, #12629, #13035, #13341, #13370, @borkmann @pchaigno)