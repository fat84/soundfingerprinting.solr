# Solr storage for audio fingerprinting framework in .NET

[![Join the chat at https://gitter.im/soundfingerprinting/Lobby](https://badges.gitter.im/soundfingerprinting/Lobby.svg)](https://gitter.im/soundfingerprinting/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

_soundfingerprinting.solr_ is [Solr](http://lucene.apache.org/solr) backend for [soundfingerprinting](https://github.com/AddictedCS/soundfingerprinting) framework. It is a very resilient, fast, non-relational storage, which allows you to scale your backend very effectively.

[![Build Status](https://travis-ci.org/AddictedCS/soundfingerprinting.solr.png)](https://travis-ci.org/AddictedCS/soundfingerprinting.solr)

### How to use
**SoundFingerprinting.Solr** uses [SorlNet](https://github.com/mausch/SolrNet) in order to connect to actual solr instances. Please provide connection string for both cores (_sf_tracks_ and _sf_fingerprints_) in your `app.config` as outlined:
```xml
<configuration>
  <configSections>
    <section name="solr" type="SoundFingerprinting.Solr.Config.SoundFingerprintingSolrConfigurationSection, SoundFingerprinting.Solr" />
  </configSections>
  <solr queryBatchSize="50" preferLocalShards="true">
    <server id="tracks" url="http://localhost:8983/solr/sf_tracks" documentType="SoundFingerprinting.Solr.DAO.TrackDTO, SoundFingerprinting.Solr" />
    <server id="fingerprints" url="http://localhost:8983/solr/sf_fingerprints" documentType="SoundFingerprinting.Solr.DAO.SubFingerprintDTO, SoundFingerprinting.Solr" />
  </solr>
</configuration>
```
### Try it with Docker

    docker pull addictedcs/soundfingerprinting.solr
	docker run -p 8983:8983 addictedcs/soundfingerprinting.solr
	
Docker image contains initialized cores and configs required for **SoundFingerprinting** framework to properly function.

### Solr schema for fingerprints and tracks
_soundfingerprinting_ audio fingerprints are stored in _sf_fingerprints_ core. It's schema can be found in `solr-config` folder. Track metadata is stored in _sf_tracks_ core.

### Disabling query result cache
It is important to disable query result cache for _sf_fingerprints_ core. You may end up with Solr memory issues otherwise.

### Third party dependencies
Links to the third party libraries used by _soundfingerprinting_ project.
* [SolrNet](https://github.com/mausch/SolrNet)
* [Ninject](http://www.ninject.org)

### Binaries
    git clone git@github.com:AddictedCS/soundfingerprinting.solr.git
    
In order to build latest version of the **SoundFingerprinting.Solr** assembly run the following command from repository root

    .\build.cmd
### Get it on NuGet

    Install-Package SoundFingerprinting.Solr -Pre
    
### Contribute
If you want to contribute you are welcome to open issues or discuss on [issues](https://github.com/AddictedCS/soundfingerprinting/issues) page. Feel free to contact me for any remarks, ideas, bug reports etc. 

### Licence
The framework is provided under [MIT](https://opensource.org/licenses/MIT) licence agreement.
