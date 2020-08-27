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
|  |  |  ├── promises.js - fs.promises的具体实现，将fs模块统一promisify化
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



## 知识点

### 整理流程

nodejs模块可以分为下面三类：

* 核心模块(native模块)：包含在 Node.js 源码中，被编译进 Node.js 可执行二进制文件 JavaScript 模块，其实也就是lib和deps目录下的js文件，比如常用的http,fs等等

* 内建模块(built-in模块)：一般我们不直接调用，而是在 native 模块中调用，然后我们再require

* 第三方模块：非 Node.js 源码自带的模块都可以统称第三方模块，比如 express，webpack 等等。

  - JavaScript 模块，这是最常见的，我们开发的时候一般都写的是 JavaScript 模块

  - JSON 模块，这个很简单，就是一个 JSON 文件

  - C/C++ 扩展模块，使用 C/C++ 编写，编译之后后缀名为 .node



比如lib目录下的fs.js就是native模块，而fs.js调用的src目录下的node_fs.cc就是内建模块。


js如何和c++联通？

<img src="https://raw.githubusercontent.com/brizer/graph-bed/master/img/20200727111557.png"/>

nodejs启动的时候调用binding::RegisterBuiltinModules()，把所有内建模块都加载到modlist_internal。

参考：

[nodejs是如何和libuv以及v8一起合作的？(文末有彩蛋哦) - 掘金](https://juejin.im/post/5dd0b1fff265da0bae519ed4)



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
