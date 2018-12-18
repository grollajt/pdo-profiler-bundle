# PDO provider for Symfony Webprofiler

This code is based on sorien/silex-dbal-profiler and maximebf/debugbar.

## Install

Composer

```bash
    composer require shamotj/pdo-profiler-bundle
```
That should add dependency into config/bundles.php. If you have service which typehints to PDO, you should be fine.
If not, you need to pass PDO instance to constructor. This can be done by overriding services.yml in your global file. 

For example like this:
```yaml
  pdo_data_collector:
    class: Shamotj\PdoProfilerBundle\DataCollector\PdoDataCollector
    arguments: ["@=service('App\\\\Service\\\\DbService').getPDO()"]
    public: false
    tags:
    - name: data_collector
      id: 'pdo_data_collector'
      template: 'ShamotjPdoProfilerBundle:Collector:db.html.twig'
```