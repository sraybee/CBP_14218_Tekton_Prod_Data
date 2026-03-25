# CBP-14218: Production Query Results

**Query Date:** March 24, 2026

**Total Resources Found:** 112 (1 TaskRun + 111 PipelineRuns)

---

## Cluster: tekton-prod-us-west-2-gree

**Resources:** 2 PipelineRuns

### TaskRuns Query
```bash
kubectl get taskruns -A -o json | jq -r '.items[] | select(.status.retriesStatus[0].provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```

**Result:** `<no-output>`

### PipelineRuns Query
```bash
kubectl get pipelineruns -A -o json | jq -r '.items[] | select(.status.provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```

**Result:**
```
event--d10ae34b8486bcd26a66e0efd1b1e6361a3a94f39492e962f396991f run-githubcom6c7c37c637a-myworkflow-b974a2738ab5663a
event-myworkflowyaml-18e37eaea264bae48ae01772e933e37de3d285c9a0 run-githubcomb50ef320379-myworkflow-b36242cd9aad4ce5
```

---

## Cluster: tekton-prod-us-west-2-blue

**Resources:** 0 (clean)

### TaskRuns Query
```bash
kubectl get taskruns -A -o json | jq -r '.items[] | select(.status.retriesStatus[0].provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```

**Result:** `<no-output>`

### PipelineRuns Query
```bash
kubectl get pipelineruns -A -o json | jq -r '.items[] | select(.status.provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```

**Result:** `<no-output>`

---

## Cluster: tekton-prod-us-east-1-blue

**Resources:** 64 (1 TaskRun + 63 PipelineRuns)

### TaskRuns Query
```bash
kubectl get taskruns -A -o json | jq -r '.items[] | select(.status.retriesStatus[0].provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```

**Result:**
```
event--6e346304378d3440a81718655a0e070ba89015c4c8a12e5f21f62163 dispatch-dispatch
```

### PipelineRuns Query
```bash
kubectl get pipelineruns -A -o json | jq -r '.items[] | select(.status.provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```

**Result:**
```
event--03db26b9c529b0826bf88f15c7dca49b451d8bc56670854db2ba5402 dispatch
event--30350b8464693ce7191a82e7e13e1a55e19df67ac86fcc6d4f4fb7ba dispatch
event--30350b8464693ce7191a82e7e13e1a55e19df67ac86fcc6d4f4fb7ba run-githubcomf7f43eee1e9-ngdispatch-c4457fcb88afc811
event--30c4771d378443d6e8fd6a1836b4a75435d99de7fdc531e18a29d221 dispatch
event--3321e6be5fcecf27c4696f468aed2b052407ea3557bc0ed066a2819f dispatch
event--3321e6be5fcecf27c4696f468aed2b052407ea3557bc0ed066a2819f run-githubcom0ca00406274-testandscan-fc08d2b833202c46
event--4941a4e5dbc86287320760210c435affd3d5960114bb190280e92f8a dispatch
event--4f92c74d57fd066a0b97b5ff4fe03763a9cd6d79906d54b3f6db6717 dispatch
event--4f92c74d57fd066a0b97b5ff4fe03763a9cd6d79906d54b3f6db6717 run-githubcombf821f04274-github-5c930004922d2885
event--4f92c74d57fd066a0b97b5ff4fe03763a9cd6d79906d54b3f6db6717 run-githubcombf821f04274-heartbeat-2ac929ddc1d239c9
event--5813f33c69d246b24c7cac5c018d9f1c031cd203ddff4f3251f8a215 dispatch
event--5813f33c69d246b24c7cac5c018d9f1c031cd203ddff4f3251f8a215 run-githubcom4e1245e2274-myworkflow-ebd7b82b73db8eb6
event--58542acd5aeadaf2f02a1325eb7abdc44ddb93720168c925b5ea0878 dispatch
event--58542acd5aeadaf2f02a1325eb7abdc44ddb93720168c925b5ea0878 run-githubcomc65f60f0220-ngdispatch-f38d368439009102
event--6b39e638a6c33c9f79ec9a3cfa38de442de72bb2ebc93aef05c2c6fc dispatch
event--6e346304378d3440a81718655a0e070ba89015c4c8a12e5f21f62163 dispatch
event--8026d900838d8057432eb608e43f6dbbae93112b44248f13b9ab24cd dispatch
event--8026d900838d8057432eb608e43f6dbbae93112b44248f13b9ab24cd run-githubcomd7e2ba8c274-myworkflow-39b90d62c27b58b3
event--817717b0097bc64315576b1d1075e51b41bc1905c5a8448b6a2a465e dispatch
event--89384a45d94fecab47501920485ef11efc6d676c5cba11d79a5e8216 dispatch
event--89384a45d94fecab47501920485ef11efc6d676c5cba11d79a5e8216 run-githubcom901fc39a1ea-ngdispatch-896eaec21ef41ceb
event--8f8e2ddd25c96071d243d2b0262a62d71537d78820d83ef5dad4a436 dispatch
event--9bc3491ef6d2ea21a2e6d18fab6a5df3fd044dd54c34697a5ce5250b dispatch
event--9bc3491ef6d2ea21a2e6d18fab6a5df3fd044dd54c34697a5ce5250b run-githubcom186cf64e274-testworkflow-c355ca0ee54cdd5a
event--a257ebee98d371000f3d0d220694251d3882bf301e896fa850b2ae87 dispatch
event--a257ebee98d371000f3d0d220694251d3882bf301e896fa850b2ae87 run-githubcom45efd0b2274-workflow-ce35d1fd0559f177
event--af738ede727e9caacc1863b8f77b6fd0e807a816a2488f94b21a529d dispatch
event--cecd949f6d057284952aca02ccae3e87cf4c397a31320bf837f18ef6 dispatch
event--cecd949f6d057284952aca02ccae3e87cf4c397a31320bf837f18ef6 run-githubcom9803fb82274-myworkflow-bc4e07b0397afc81
event--fba9830ddd24659be2d2603b261adef0cb1d2e9c8d4a756c2d49a18c dispatch
event--fba9830ddd24659be2d2603b261adef0cb1d2e9c8d4a756c2d49a18c run-githubcom00c07378274-deploy-961e7d68863c7823
event-aspmyaml-6f3896c77da741036c1c60b930d7a6da267368b655937564 dispatch
event-aspmyaml-6f3896c77da741036c1c60b930d7a6da267368b655937564 run-schedule3e1929a2ec32-aspm-bfd1f7190c1b1ec9
event-betayaml-13e0621bbb6cdd5791ab5226348c2a69d9afa5a58f992748 dispatch
event-betayaml-13e0621bbb6cdd5791ab5226348c2a69d9afa5a58f992748 run-schedule2f35690868d3-beta-6d1bf7e145916c3e
event-cloudbeesscannersbinaryscanyaml-c396fcec39618a907890e38d8 dispatch
event-cloudbeesscannersbinaryscanyaml-c396fcec39618a907890e38d8 run-dispatch0095aae42959-binaryscan-c50956d027c077c4
event-cloudbeesscannersbinaryscanyaml-f2eb6b6e68e53a105d90590ba dispatch
event-cloudbeesscannersbinaryscanyaml-f2eb6b6e68e53a105d90590ba run-dispatch0fb4e8128706-binaryscan-11bb86a24afb02d5
event-cloudbeesscannerscodescanyaml-006c883ab54dbf7a728e35c4b77 dispatch
event-cloudbeesscannerscodescanyaml-006c883ab54dbf7a728e35c4b77 run-dispatche80e3157b2aa-codescan-cf9933dfaddd90ca
event-cloudbeesscannerscodescanyaml-052608bef8d0a7ac551c167de68 dispatch
event-cloudbeesscannerscodescanyaml-052608bef8d0a7ac551c167de68 run-dispatch170ec4e0feaf-codescan-8be384f2be352035
event-cloudbeesscannerscodescanyaml-1108e2ace0a3c49665b70108e52 dispatch
event-cloudbeesscannerscodescanyaml-1108e2ace0a3c49665b70108e52 run-dispatch30e581120956-codescan-8519d22a91fde90b
event-cloudbeesscannerscodescanyaml-506f845926a52768108597d7a43 dispatch
event-cloudbeesscannerscodescanyaml-506f845926a52768108597d7a43 run-dispatch231a94fbeb70-codescan-3eca4fdfa6305c33
event-cloudbeesscannerscodescanyaml-691fc0bfee589c007e8b892ae98 dispatch
event-cloudbeesscannerscodescanyaml-691fc0bfee589c007e8b892ae98 run-dispatch71062a400ffb-codescan-77bd5dbbe2a131f7
event-cloudbeesscannerscodescanyaml-91649a8a60a4cf005384b10b801 dispatch
event-cloudbeesscannerscodescanyaml-91649a8a60a4cf005384b10b801 run-dispatchf40b57d54b58-codescan-2de7cf11744c27f6
event-cloudbeesscannerscodescanyaml-b9591ec194f78cb6ed05ad92609 dispatch
event-cloudbeesscannerscodescanyaml-b9591ec194f78cb6ed05ad92609 run-dispatchef36abe7b89f-codescan-cb22d16bdd3241f6
event-cloudbeesscannerscodescanyaml-ec496e6cd7e157c381cf84a8171 dispatch
event-cloudbeesscannerscodescanyaml-ec496e6cd7e157c381cf84a8171 run-dispatch2817eefca1fb-codescan-e43e3920dc93f4b4
event-productionreleaseyaml-2f76c1eb20941d58a591b270144d866d489 dispatch
event-productionreleaseyaml-2f76c1eb20941d58a591b270144d866d489 run-dispatch4a230984ab91-productionrelease-29ee92a692948476
event-productionreleaseyaml-ccdb2cc9e0fc1f54570c0b5839738099d2b dispatch
event-productionreleaseyaml-ccdb2cc9e0fc1f54570c0b5839738099d2b run-dispatch5ea3d5a161a0-productionrelease-282fe17e02b780f5
event-queuemanagementyaml-0792a3ecc6a0c2cc57cc3c1f2a8f63b3605a0 dispatch
event-queuemanagementyaml-0792a3ecc6a0c2cc57cc3c1f2a8f63b3605a0 run-schedule16581fee028b-queuemanagement-cedd0ee329500ecb
event-scheduledworkflowyaml-08f10a3fad828d7cc6f0e5a69467572f6cf dispatch
event-scheduledworkflowyaml-08f10a3fad828d7cc6f0e5a69467572f6cf run-schedule2bc5ba4f0c62-scheduledworkflow-9824b51065decd33
```

---

## Cluster: tekton-prod-us-east-1-gree

**Resources:** 46 PipelineRuns

### TaskRuns Query
```bash
kubectl get taskruns -A -o json | jq -r '.items[] | select(.status.retriesStatus[0].provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```

**Result:** `<no-output>`

### PipelineRuns Query
```bash
kubectl get pipelineruns -A -o json | jq -r '.items[] | select(.status.provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```

**Result:**
```
event--10d2907316d149e25afeaec66cedffd3c50eb092f09fe4935e27bb50 dispatch
event--19a924fc56cf82caa10244c53c8f7d001e24a35dbe8d1c49078d0bf4 dispatch
event--1b3003bbbe2f431bd9b287fc4b6401ff5feb1b2eb407bdda519e8446 dispatch
event--2c50bf57397b10169e0b4fa2fc3b77fd26375a6bf7bb7ac2282b93bf dispatch
event--3ff6496f0a2cf7268fc405dea39ca7a93debafa894417a2b37fd5d9e dispatch
event--46b2d1d6528c52e3519f29979a1baabc38b30193b6b878673e898653 dispatch
event--55db8eeb1e2cb6b4a6bbad504298ba550b124f4375d42c2e3c5c9b93 dispatch
event--5f34a115672adfcc7ed7f28138420b1970704e30d0916416c74fa82d dispatch
event--5f34a115672adfcc7ed7f28138420b1970704e30d0916416c74fa82d run-githubcom0b3dc0b6274-deploy-c66dfcea20b5feb5
event--62a9dca2cf5c04466f17ab7a19675ca7a3a83480db10207073a4c04c dispatch
event--743fa4ff47da213614e2daab12ce69c2f29af9f5669b8706211dd837 dispatch
event--7642baff306c2827cecaa78948bef3253f47ef9ec1d3f2bdd51b7701 dispatch
event--7dce86070418a4c2cf500a728a335ca4c103f956b7bcf38efe8f01d6 dispatch
event--8615e2d811d0f0c2d22bb0c315367046e91aac64412fe3d907258fb4 dispatch
event--8692c3c24d456526c3a4851cd7f2a68d4b0fab43e705eea10fe7676f run-githubcom8d7541de37a-myworkflow-b88e09e3c3a7ed01
event--a094a6ec2b08e8195d35487ef219a33dc7e49d94cff3528975c2faa7 dispatch
event--a610159712aa70686e37277d64ee42e8b9e6d94c52a7b6f93b5555fe dispatch
event--b0ccac06b2beab513223e91629a8d2891e1695519c2445aece99bcad dispatch
event--b0ccac06b2beab513223e91629a8d2891e1695519c2445aece99bcad run-githubcomd2334e5c274-build-60d4e2f5dfc7a5ed
event--b0ccac06b2beab513223e91629a8d2891e1695519c2445aece99bcad run-githubcomd2334e5c274-deploy-cb4686bac701059f
event--bc51023a96d41edf9e53d8ae900f8d8b39a4c704abc60e09ce667405 dispatch
event--bc51023a96d41edf9e53d8ae900f8d8b39a4c704abc60e09ce667405 run-githubcomc458934c1e9-ngdispatch-519a26a9b2273ea3
event--c20ac9d6fcd187cdd4ee03e892df0a56911de2d0e7ad4aade4862be4 dispatch
event--c20ac9d6fcd187cdd4ee03e892df0a56911de2d0e7ad4aade4862be4 run-githubcomf9536752274-github-f5fcf5037a5d13e0
event--c20ac9d6fcd187cdd4ee03e892df0a56911de2d0e7ad4aade4862be4 run-githubcomf9536752274-heartbeat-69478b6358d7ed90
event--c6b24e7442ae5857cb07c5b945d044779e016bb94aaf5df745a96d49 dispatch
event--c6b24e7442ae5857cb07c5b945d044779e016bb94aaf5df745a96d49 run-githubcom56fcff8a273-deploy-dc0b43d7f1a14d02
event--f5bc71936fdef8c62dd79d44e20e41e88a49e4907935db2e1a9acfca dispatch
event--f7c691cd4c7ea82a0180985aa90c6bb609ec4e93eecf9bde19bcf9b8 dispatch
event--f7c691cd4c7ea82a0180985aa90c6bb609ec4e93eecf9bde19bcf9b8 run-githubcom8edb492a274-build-a9f19d1fa9c2d2d4
event--f7c691cd4c7ea82a0180985aa90c6bb609ec4e93eecf9bde19bcf9b8 run-githubcom8edb492a274-deploy-b8831e33d84b5886
event-cloudbeesscannerscodescanyaml-087f4c1d4198a99aa9a724b1796 dispatch
event-cloudbeesscannerscodescanyaml-087f4c1d4198a99aa9a724b1796 run-dispatchfea1cb22b372-codescan-442eb68cd08c00b3
event-cloudbeesscannerscodescanyaml-6a7c40f470b0cec0125cef84478 dispatch
event-cloudbeesscannerscodescanyaml-6a7c40f470b0cec0125cef84478 run-dispatch2f161e4982ca-codescan-85132adf39106c7b
event-cloudbeesscannerscodescanyaml-72c7396b1a4dca84607c5e1b2f7 dispatch
event-cloudbeesscannerscodescanyaml-72c7396b1a4dca84607c5e1b2f7 run-dispatch1188eb8caa5d-codescan-0506d994ca45c7ef
event-cloudbeesscannerscodescanyaml-a718716a977ccfdf8cacce20838 dispatch
event-cloudbeesscannerscodescanyaml-a718716a977ccfdf8cacce20838 run-dispatch4b0edf4fd28f-codescan-34439c7b7b1b8b0e
event-cloudbeesscannerscodescanyaml-d0e61d53d85499f67d6b6916c60 dispatch
event-queuemanagementyaml-a9cd89e65f62e2ec8859ef72a605df2e04c4a dispatch
event-queuemanagementyaml-a9cd89e65f62e2ec8859ef72a605df2e04c4a run-scheduleceac120bbe4f-queuemanagement-4874bc19deadca53
event-scheduledworkflowyaml-2eeb59e94503dea408765564209cbf39961 dispatch
event-scheduledworkflowyaml-2eeb59e94503dea408765564209cbf39961 run-schedule443200c25195-scheduledworkflow-0f826f39fd77b498
event-unifyciyaml-f3bc19cbe04484816160f385a54b4e9156b4842762517 dispatch
event-unifyciyaml-f3bc19cbe04484816160f385a54b4e9156b4842762517 run-scheduled37a6c871b20-unifyci-c1b8342965ae5700
```

---

## Summary

| Cluster | TaskRuns | PipelineRuns | Total |
|---------|----------|--------------|-------|
| tekton-prod-us-west-2-gree | 0 | 2 | 2 |
| tekton-prod-us-west-2-blue | 0 | 0 | 0 |
| tekton-prod-us-east-1-blue | 1 | 63 | 64 |
| tekton-prod-us-east-1-gree | 0 | 46 | 46 |
| **TOTAL** | **1** | **111** | **112** |
