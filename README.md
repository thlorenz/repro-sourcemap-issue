# repro sourcemap issue

This repro exists to show an example of reproducing an issue when bundling with browserify with source maps enabled and
using es6ify as a transform.

In order to reproduce it clone this repo and do:

`npm install && npm test`


You'll get a stacktrace similar to this one:

```sh
/Users/thlorenz/dev/js/projects/es6ify/tmp/node_modules/browserify/node_modules/browser-pack/node_modules/combine-source-map/node_modules/source-map/lib/source-map/array-set.js:83
    throw new Error('No element indexed by ' + aIdx);
          ^
Error: No element indexed by 1
    at ArraySet_at [as at] (/Users/thlorenz/dev/js/projects/es6ify/tmp/node_modules/browserify/node_modules/browser-pack/node_modules/combine-source-map/node_modules/source-map/lib/source-map/array-set.js:83:11)
    at SourceMapConsumer_parseMappings [as _parseMappings] (/Users/thlorenz/dev/js/projects/es6ify/tmp/node_modules/browserify/node_modules/browser-pack/node_modules/combine-source-map/node_modules/source-map/lib/source-map/source-map-consumer.js:158:44)
    at new SourceMapConsumer (/Users/thlorenz/dev/js/projects/es6ify/tmp/node_modules/browserify/node_modules/browser-pack/node_modules/combine-source-map/node_modules/source-map/lib/source-map/source-map-consumer.js:100:10)
    at module.exports (/Users/thlorenz/dev/js/projects/es6ify/tmp/node_modules/browserify/node_modules/browser-pack/node_modules/combine-source-map/lib/mappings-from-map.js:10:18)
    at Combiner._addExistingMap (/Users/thlorenz/dev/js/projects/es6ify/tmp/node_modules/browserify/node_modules/browser-pack/node_modules/combine-source-map/index.js:28:18)
    at Combiner.addFile (/Users/thlorenz/dev/js/projects/es6ify/tmp/node_modules/browserify/node_modules/browser-pack/node_modules/combine-source-map/index.js:58:12)
    at Stream.write (/Users/thlorenz/dev/js/projects/es6ify/tmp/node_modules/browserify/node_modules/browser-pack/index.js:42:23)
    at Stream.stream.write (/Users/thlorenz/dev/js/projects/es6ify/tmp/node_modules/browserify/node_modules/through/index.js:26:11)
    at Stream.ondata (stream.js:51:26)
    at Stream.EventEmitter.emit (events.js:95:17)
```

However if source maps are turned off things work just fine. You can confirm that via: `npm run test-no-sourcemap`.
