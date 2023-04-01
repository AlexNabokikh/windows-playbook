# Changelog

All notable changes to this project will be documented in this file.

## [2.0.1](https://github.com/AlexNabokikh/windows-playbook/compare/v2.0.0...v2.0.1) (2023-04-01)


### Bug Fixes

* **storage_sense:** fixed incorrect when conditions ([03e518f](https://github.com/AlexNabokikh/windows-playbook/commit/03e518f9511c1534754c6d8b933f3fedc6d93f33))

## [2.0.0](https://github.com/AlexNabokikh/windows-playbook/compare/v1.15.0...v2.0.0) (2023-03-31)


### ⚠ BREAKING CHANGES

* **main.yml:** chocolatey and winget packages installation are now
optional. Please make changes in your configs accordingly.

### Features

* **storage:** added a task that enables storage sense ([cd9d5b1](https://github.com/AlexNabokikh/windows-playbook/commit/cd9d5b1592b617c663eb2093a5453edcbc55e969))


### Bug Fixes

* **deps:** bumped pipeline dependecies ([0b46840](https://github.com/AlexNabokikh/windows-playbook/commit/0b46840e6e33ae8ae2199eadb794cba2aa2eaa06))
* **remote_desktop:** forbidden implicit octal value ([edcfc54](https://github.com/AlexNabokikh/windows-playbook/commit/edcfc54e367558f4a917ba2ccf7b8766ab972a58))
* **storage:** too many spaces inside braces ([9dd1d15](https://github.com/AlexNabokikh/windows-playbook/commit/9dd1d15de3b5b47cc837c9b0581fda697b303f1e))


### Miscellaneous Chores

* **main.yml:** revorked playbook entrypoint ([f833db7](https://github.com/AlexNabokikh/windows-playbook/commit/f833db70a231cf4d04ed7cfd2819448a58af9b33))

## [1.15.0](https://github.com/AlexNabokikh/windows-playbook/compare/v1.14.1...v1.15.0) (2022-12-12)


### Features

* change task names wording ([99a3dce](https://github.com/AlexNabokikh/windows-playbook/commit/99a3dceaca22dc2960ffc3a136ede86dcf74a087))
* **power_plan:** ensure the plan set correctly even if system language is not english ([10a36cb](https://github.com/AlexNabokikh/windows-playbook/commit/10a36cb857b18da47a6d1d031b32e2f809bdaae1))
* **winget:** introduced winget package installation task ([098186c](https://github.com/AlexNabokikh/windows-playbook/commit/098186c1e89e257a3fc59ca867942257e742a07b))


### Bug Fixes

* **license:** fixed license date ([bf4e847](https://github.com/AlexNabokikh/windows-playbook/commit/bf4e847ba26a943266d958965057feee992a2cb0))

## [1.14.1](https://github.com/AlexNabokikh/windows-playbook/compare/v1.14.0...v1.14.1) (2022-12-11)


### Bug Fixes

* **wsl2:** fixed task name ([1fc7ce1](https://github.com/AlexNabokikh/windows-playbook/commit/1fc7ce1558708bed417bed1c1071a2326395a8d5))

## [1.14.0](https://github.com/AlexNabokikh/windows-playbook/compare/v1.13.1...v1.14.0) (2022-09-03)


### Features

* **default.config:** adjusted the default config with more sane parameters ([e390c50](https://github.com/AlexNabokikh/windows-playbook/commit/e390c50192d13a0a47f5be24dc87546ee0de7e74))


### Bug Fixes

* **main:** added missed when parameter for the remote desktop task ([34ef92f](https://github.com/AlexNabokikh/windows-playbook/commit/34ef92f13eb15ac128eb32189de740b3536b327c))

### [1.13.1](https://github.com/AlexNabokikh/windows-playbook/compare/v1.13.0...v1.13.1) (2022-08-21)


### Bug Fixes

* **chocolatey:** allow the cache cleaner task to continue if the cache is busy ([fe78ccc](https://github.com/AlexNabokikh/windows-playbook/commit/fe78ccc221d4bb11435a8edb984e3d16e726edb7))

## [1.13.0](https://github.com/AlexNabokikh/windows-playbook/compare/v1.12.0...v1.13.0) (2022-08-15)


### Features

* **explorer.yml:** reformated task's code ([f79f1e6](https://github.com/AlexNabokikh/windows-playbook/commit/f79f1e6c50d9bdabf6f615ffe15a5976c458b85b))
* **power_plan:** added default value for power_plan ([e9b537a](https://github.com/AlexNabokikh/windows-playbook/commit/e9b537adca33e69321d29cc3a4939d5075029c70))
* **setup.ps1:** added powershell execution policy setup step ([812a485](https://github.com/AlexNabokikh/windows-playbook/commit/812a485d78ad5d0e294e53d43c3bc16878528bde))


### Bug Fixes

* **ohmyposh:** Ensure task won't fail because the PowerShell profile does not exist. ([b30ae1e](https://github.com/AlexNabokikh/windows-playbook/commit/b30ae1ee224a165891f1a1ffa18a4f5d7f2b7acc))

## [1.12.0](https://github.com/AlexNabokikh/windows-playbook/compare/v1.11.0...v1.12.0) (2022-08-10)


### Features

* **desktop.yml:** limit desktop cleanup to shortcuts only ([324fb27](https://github.com/AlexNabokikh/windows-playbook/commit/324fb2759f64ee21f8746803050c4a0df4efafeb))


### Bug Fixes

* **desktop.yml:** fixed typo ([3cbf360](https://github.com/AlexNabokikh/windows-playbook/commit/3cbf360951cc9ab190dddea91fd5e4c924f14fb4))

## [1.11.0](https://github.com/AlexNabokikh/windows-playbook/compare/v1.10.0...v1.11.0) (2022-08-10)


### Features

* **chocolatey:** improved choco packages installation task ([086473c](https://github.com/AlexNabokikh/windows-playbook/commit/086473cd96fa66db3071f8f5c5a8247a9ef05eb8))


### Bug Fixes

* **lint:** addressed yamllint warnings ([46a61b3](https://github.com/AlexNabokikh/windows-playbook/commit/46a61b39a28185b32ce053372813ff02533b3f17))

## [1.10.0](https://github.com/AlexNabokikh/windows-playbook/compare/v1.9.0...v1.10.0) (2022-08-09)


### Features

* **windows_updates:** improved windows updates installation task ([be2c975](https://github.com/AlexNabokikh/windows-playbook/commit/be2c975cc41ccb782a54c88b841a4e4a91ccad52))

## [1.9.0](https://github.com/AlexNabokikh/windows-playbook/compare/v1.8.0...v1.9.0) (2022-07-31)


### Features

* added oh-my-posh as a prompt theme engine for powershell ([b561390](https://github.com/AlexNabokikh/windows-playbook/commit/b561390f674d03c2bd03861c149ef7d256df1d76))
* **README.md:** added oh-my-posh theme change example ([63246f9](https://github.com/AlexNabokikh/windows-playbook/commit/63246f917ce84b288dd666ff5bb884d39f513cb8))
* replaced 7zip with the modern alternative ([222339e](https://github.com/AlexNabokikh/windows-playbook/commit/222339ee9c74f9c2be8d8e375cf89ff09b25cdb9))


### Bug Fixes

* **ohmyposh.yml:** replaced yes with true ([bde9253](https://github.com/AlexNabokikh/windows-playbook/commit/bde9253e068406de0079b828b3aea4a56a79152e))

## [1.8.0](https://github.com/AlexNabokikh/windows-playbook/compare/v1.7.1...v1.8.0) (2022-06-16)


### Features

* **.ansible-lint:** adjusted linter settings ([d8ef644](https://github.com/AlexNabokikh/windows-playbook/commit/d8ef6441f5e1ef0e0a1650a6994459615af371bd))

### [1.7.1](https://github.com/AlexNabokikh/windows-playbook/compare/v1.7.0...v1.7.1) (2022-06-16)


### Bug Fixes

* refactored modules definition according to best practices ([ae228a9](https://github.com/AlexNabokikh/windows-playbook/commit/ae228a9a486c687c47005d0f37d63b8bdd95ab97))

## [1.7.0](https://github.com/AlexNabokikh/windows-playbook/compare/v1.6.1...v1.7.0) (2022-06-13)


### Features

* **.yamllint.yml:** ignore github ci yaml during lint stage ([0d7fdc6](https://github.com/AlexNabokikh/windows-playbook/commit/0d7fdc67fffcb794ddd61a453f1b65df20160939))
* added 'defragment' task to the main config ([5779595](https://github.com/AlexNabokikh/windows-playbook/commit/57795954c50b9c9ea76e3744f9b0de128a5b970e))
* **chocolatey.yml:** added chocolatey and nuget cache clear task ([921b511](https://github.com/AlexNabokikh/windows-playbook/commit/921b5111caa87428e19d30d3ac79b61ab893e43e))
* **defrag.yml:** added 'defragment' task ([24016c8](https://github.com/AlexNabokikh/windows-playbook/commit/24016c8a75e1f6d7087147a0ec341c61944bbdf7))
* **updates.yml:** set 'state' explicitly for better readability ([7c66404](https://github.com/AlexNabokikh/windows-playbook/commit/7c66404dcacb312319c37dafcb5eeb67487e986e))


### Bug Fixes

* **defrag.yml:** fixed default value for valumes ([dc0ecbc](https://github.com/AlexNabokikh/windows-playbook/commit/dc0ecbcab409880904d42be5125cc66e518693af))

### [1.6.1](https://github.com/AlexNabokikh/windows-playbook/compare/v1.6.0...v1.6.1) (2022-06-12)


### Bug Fixes

* **README.md:** fixed badges and applied MD best practices ([525c805](https://github.com/AlexNabokikh/windows-playbook/commit/525c80556767ead48d5e82df527cade2348498b2))
* **README.md:** fixed gh badge link ([b253e6a](https://github.com/AlexNabokikh/windows-playbook/commit/b253e6a2dae5c30d0b287e322676f7fd6b63ca7a))

## [1.6.0](https://github.com/AlexNabokikh/windows-playbook/compare/v1.5.1...v1.6.0) (2022-05-27)


### Features

* added automatic semantic-release ([b3645ff](https://github.com/AlexNabokikh/windows-playbook/commit/b3645ffb70fb0545be9b37c867c119f6777c6a96))
