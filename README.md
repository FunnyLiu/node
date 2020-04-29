# 源码分析

## 文件结构

### lib文件下node层相关

``` bash
├── lib
|  ├── _http_agent.js
|  ├── _http_client.js
|  ├── _http_common.js
|  ├── _http_incoming.js
|  ├── _http_outgoing.js
|  ├── _http_server.js
|  ├── _stream_duplex.js
|  ├── _stream_passthrough.js
|  ├── _stream_readable.js
|  ├── _stream_transform.js
|  ├── _stream_wrap.js
|  ├── _stream_writable.js
|  ├── _tls_common.js
|  ├── _tls_wrap.js
|  ├── assert.js
|  ├── async_hooks.js
|  ├── buffer.js
|  ├── child_process.js
|  ├── cluster.js
|  ├── console.js
|  ├── constants.js
|  ├── crypto.js
|  ├── dgram.js
|  ├── dns.js
|  ├── domain.js
|  ├── events.js
|  ├── fs.js
|  ├── http.js
|  ├── http2.js
|  ├── https.js
|  ├── inspector.js
|  ├── internal
|  |  ├── assert
|  |  |  └── assertion_error.js
|  |  ├── assert.js
|  |  ├── async_hooks.js
|  |  ├── bootstrap
|  |  |  ├── environment.js
|  |  |  ├── loaders.js
|  |  |  ├── node.js
|  |  |  ├── pre_execution.js
|  |  |  └── switches
|  |  |     ├── does_not_own_process_state.js
|  |  |     ├── does_own_process_state.js
|  |  |     ├── is_main_thread.js
|  |  |     └── is_not_main_thread.js
|  |  ├── buffer.js
|  |  ├── child_process
|  |  |  └── serialization.js
|  |  ├── child_process.js
|  |  ├── cli_table.js
|  |  ├── cluster
|  |  |  ├── child.js
|  |  |  ├── master.js
|  |  |  ├── round_robin_handle.js
|  |  |  ├── shared_handle.js
|  |  |  ├── utils.js
|  |  |  └── worker.js
|  |  ├── console
|  |  |  ├── constructor.js
|  |  |  └── global.js
|  |  ├── constants.js
|  |  ├── crypto
|  |  |  ├── certificate.js
|  |  |  ├── cipher.js
|  |  |  ├── diffiehellman.js
|  |  |  ├── hash.js
|  |  |  ├── keygen.js
|  |  |  ├── keys.js
|  |  |  ├── pbkdf2.js
|  |  |  ├── random.js
|  |  |  ├── scrypt.js
|  |  |  ├── sig.js
|  |  |  └── util.js
|  |  ├── dgram.js
|  |  ├── dns
|  |  |  ├── promises.js
|  |  |  └── utils.js
|  |  ├── dtrace.js
|  |  ├── encoding.js
|  |  ├── error-serdes.js
|  |  ├── errors.js
|  |  ├── fixed_queue.js
|  |  ├── freelist.js
|  |  ├── freeze_intrinsics.js
|  |  ├── fs
|  |  |  ├── dir.js
|  |  |  ├── promises.js
|  |  |  ├── read_file_context.js
|  |  |  ├── rimraf.js
|  |  |  ├── streams.js
|  |  |  ├── sync_write_stream.js
|  |  |  ├── utils.js
|  |  |  └── watchers.js
|  |  ├── http.js
|  |  ├── http2
|  |  |  ├── compat.js
|  |  |  ├── core.js
|  |  |  └── util.js
|  |  ├── idna.js
|  |  ├── inspector_async_hook.js
|  |  ├── js_stream_socket.js
|  |  ├── linkedlist.js
|  |  ├── main
|  |  |  ├── check_syntax.js
|  |  |  ├── eval_stdin.js
|  |  |  ├── eval_string.js
|  |  |  ├── inspect.js
|  |  |  ├── print_help.js
|  |  |  ├── prof_process.js
|  |  |  ├── repl.js
|  |  |  ├── run_main_module.js
|  |  |  ├── run_third_party_main.js
|  |  |  └── worker_thread.js
|  |  ├── modules
|  |  |  ├── cjs
|  |  |  |  ├── helpers.js
|  |  |  |  └── loader.js - 模块的处理逻辑，require的原理就在此处
|  |  |  ├── esm
|  |  |  |  ├── create_dynamic_module.js
|  |  |  |  ├── get_format.js
|  |  |  |  ├── get_source.js
|  |  |  |  ├── loader.js
|  |  |  |  ├── module_job.js
|  |  |  |  ├── module_map.js
|  |  |  |  ├── resolve.js
|  |  |  |  ├── transform_source.js
|  |  |  |  └── translators.js
|  |  |  └── run_main.js
|  |  ├── net.js
|  |  ├── options.js
|  |  ├── per_context
|  |  |  ├── domexception.js
|  |  |  └── primordials.js
|  |  ├── policy
|  |  |  ├── manifest.js
|  |  |  └── sri.js
|  |  ├── priority_queue.js
|  |  ├── process
|  |  |  ├── esm_loader.js
|  |  |  ├── execution.js
|  |  |  ├── per_thread.js
|  |  |  ├── policy.js
|  |  |  ├── promises.js
|  |  |  ├── report.js
|  |  |  ├── signal.js
|  |  |  ├── task_queues.js
|  |  |  ├── warning.js
|  |  |  └── worker_thread_only.js
|  |  ├── querystring.js
|  |  ├── readline
|  |  |  └── utils.js
|  |  ├── readme.md
|  |  ├── repl
|  |  |  ├── await.js
|  |  |  ├── history.js
|  |  |  └── utils.js
|  |  ├── repl.js
|  |  ├── socket_list.js
|  |  ├── source_map
|  |  |  ├── prepare_stack_trace.js
|  |  |  ├── source_map.js
|  |  |  └── source_map_cache.js
|  |  ├── stream_base_commons.js
|  |  ├── streams
|  |  |  ├── async_iterator.js
|  |  |  ├── buffer_list.js
|  |  |  ├── destroy.js
|  |  |  ├── duplexpair.js
|  |  |  ├── end-of-stream.js
|  |  |  ├── from.js
|  |  |  ├── lazy_transform.js
|  |  |  ├── legacy.js
|  |  |  ├── pipeline.js
|  |  |  └── state.js
|  |  ├── timers.js
|  |  ├── tls.js
|  |  ├── trace_events_async_hooks.js
|  |  ├── tty.js
|  |  ├── url.js
|  |  ├── util
|  |  |  ├── comparisons.js
|  |  |  ├── debuglog.js
|  |  |  ├── inspect.js
|  |  |  ├── inspector.js
|  |  |  └── types.js
|  |  ├── util.js
|  |  ├── v8_prof_polyfill.js
|  |  ├── v8_prof_processor.js
|  |  ├── validators.js
|  |  ├── vm
|  |  |  └── module.js
|  |  ├── worker
|  |  |  └── io.js
|  |  └── worker.js
|  ├── module.js
|  ├── net.js
|  ├── os.js
|  ├── path.js
|  ├── perf_hooks.js
|  ├── process.js
|  ├── punycode.js
|  ├── querystring.js
|  ├── readline.js
|  ├── repl.js
|  ├── stream.js
|  ├── string_decoder.js
|  ├── sys.js
|  ├── timers.js
|  ├── tls.js
|  ├── trace_events.js
|  ├── tty.js
|  ├── url.js
|  ├── util.js
|  ├── v8.js
|  ├── vm.js
|  ├── wasi.js
|  ├── worker_threads.js
|  └── zlib.js
├── node.gyp
├── node.gypi

```



## 逐个文件分析

### lib/internal/modules/cjs/loader.js

模块的处理逻辑，require的原理就在此处，模块的加载实质上就是，注入exports、require、module三个全局变量，然后执行模块的源码，然后将模块的 exports 变量的值输出。

中间会去Module._cache中查找缓存看是否存在该模块内容。

入口在`Module.prototype.require`中。最后的出口在：

``` javascript
// require的原理
let wrap = function(script) {
  return Module.wrapper[0] + script + Module.wrapper[1];
};
// 将加载的js文件内容包装后立即执行
// 模块的加载实质上就是，注入exports、require、module三个全局变量，然后执行模块的源码，然后将模块的 exports 变量的值输出。
const wrapper = [
  '(function (exports, require, module, __filename, __dirname) { ',
  '\n});'
];
```
