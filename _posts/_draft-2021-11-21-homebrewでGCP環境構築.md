---
title: homebrewでGCP~terraformで環境構築
layout: post
---


ike@smallShip ~ % 
ike@smallShip ~ % 

```bash
ike@smallShip ~ % gcloud init 
Welcome! This command will take you through the configuration of gcloud.

Your current configuration has been set to: [default]

You can skip diagnostics next time by using the following flag:
  gcloud init --skip-diagnostics

Network diagnostic detects and fixes local network connection issues.
Checking network connection...done.                                                                      
Reachability Check passed.
Network diagnostic passed (1/1 checks passed).

You must log in to continue. Would you like to log in (Y/n)?  Y

Your browser has been opened to visit:

    https://accounts.google.com/o/oauth2/auth?response_type=code&client_id=32555940559.apps.googleusercontent.com&redirect_uri=http%3A%2F%2Flocalhost%3A8085%2F&scope=openid+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fuserinfo.email+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcloud-platform+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fappengine.admin+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Fcompute+https%3A%2F%2Fwww.googleapis.com%2Fauth%2Faccounts.reauth&state=LExbrSWaqhJ4bflmmJtUmjVUQHfuK1&access_type=offline&code_challenge=NcLjzO2sq-eKlKALPs4YpjwzJLo_dQ_Y-YQ7W0ON8s0&code_challenge_method=S256

You are logged in as: [ikmonjara2rnmt@gmail.com].

Pick cloud project to use: 
 [1] amongus-ike-tool
 [2] chabudai-en-liff
 [3] chabudai-en-liff-staging
 [4] line-admin-test
 [5] museulium-api-express3
 [6] museulium-cb08f
 [7] yaecho-tokyo01
 [8] Create a new project
Please enter numeric choice or text value (must exactly match list item):  8

Enter a Project ID. Note that a Project ID CANNOT be changed later.
Project IDs must be 6-30 characters (lowercase ASCII, digits, or
hyphens) in length and start with a lowercase letter. ike-gcloud-test
Waiting for [operations/cp.6796373560208365780] to finish...done.                                        
Your current project has been set to: [ike-gcloud-test].

Not setting default zone/region (this feature makes it easier to use
[gcloud compute] by setting an appropriate default value for the
--zone and --region flag).
See https://cloud.google.com/compute/docs/gcloud-compute section on how to set
default compute region and zone manually. If you would like [gcloud init] to be
able to do this for you the next time you run it, make sure the
Compute Engine API is enabled for your project on the
https://console.developers.google.com/apis page.

Created a default .boto configuration file at [/Users/ike/.boto]. See this file and
[https://cloud.google.com/storage/docs/gsutil/commands/config] for more
information about configuring Google Cloud Storage.
Your Google Cloud SDK is configured and ready to use!

* Commands that require authentication will use ikmonjara2rnmt@gmail.com by default
* Commands will reference project `ike-gcloud-test` by default
Run `gcloud help config` to learn how to change individual settings

This gcloud configuration is called [default]. You can create additional configurations if you work with multiple accounts and/or projects.
Run `gcloud topic configurations` to learn more.

Some things to try next:

* Run `gcloud --help` to see the Cloud Platform services you can interact with. And run `gcloud help COMMAND` to get help on any gcloud command.
* Run `gcloud topic --help` to learn about advanced features of the SDK like arg files and output formatting
```

確認コマンド
`$ gcloud config configurations list` 

リージョンとゾーンが設定されていない

デフォルトで使うリージョン/ゾーンの設定コマンド
```
$ gcloud compute project-info add-metadata \
    --metadata google-compute-default-region=asia-northeast1,google-compute-default-zone=asia-northeast1-c
```

請求先が見つからないと言われた
```
ERROR: (gcloud.compute.project-info.add-metadata) FAILED_PRECONDITION: Billing account for project 'XXXXXXXXXX' is not found. Billing must be enabled for activation of service(s) 'compute.googleapis.com,compute.googleapis.com,compute.googleapis.com' to proceed.
```

Webコンソールからぽちぽちと請求先を設定。

再び以下のコマンドを実施
```
$ gcloud compute project-info add-metadata \
    --metadata google-compute-default-region=asia-northeast1,google-compute-default-zone=asia-northeast1-c
```

```
$ gcloud config configurations list
```

先ほど作成したプロジェクトではまだリージョン/ゾーンの設定が有効になっていないことが確認できた。

再びぽちぽち。
```
$ gcloud init
```

```
$ gcloud config configurations list
```

プロジェクトにリージョン/ゾーンの反映ができた。
