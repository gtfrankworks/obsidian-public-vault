## 1. 在mac终端安装出现的问题

```
Goodbye! ⚕  
Traceback (most recent call last):  
  File "/Users/frank/.local/share/uv/python/cpython-3.11.15-macos-aarch64-none/lib/python3.11/asyncio/selector_events.py", line 269, in _add_reader  
    key = self._selector.get_key(fd)  
          ^^^^^^^^^^^^^^^^^^^^^^^^^^  
  File "/Users/frank/.local/share/uv/python/cpython-3.11.15-macos-aarch64-none/lib/python3.11/selectors.py", line 192, in get_key  
    raise KeyError("{!r} is not registered".format(fileobj)) from None  
KeyError: '0 is not registered'  
​  
During handling of the above exception, another exception occurred:  
​  
Traceback (most recent call last):  
  File "/Users/frank/.local/bin/hermes", line 10, in <module>  
    sys.exit(main())  
             ^^^^^^  
  File "/Users/frank/.hermes/hermes-agent/hermes_cli/main.py", line 9930, in main  
    args.func(args)  
  File "/Users/frank/.hermes/hermes-agent/hermes_cli/main.py", line 1219, in cmd_chat  
    cli_main(**kwargs)  
  File "/Users/frank/.hermes/hermes-agent/cli.py", line 11132, in main  
    cli.run()  
  File "/Users/frank/.hermes/hermes-agent/cli.py", line 10780, in run  
    app.run()  
  File "/Users/frank/.hermes/hermes-agent/venv/lib/python3.11/site-packages/prompt_toolkit/application/application.py", line 1002, in run  
    return asyncio.run(coro)  
           ^^^^^^^^^^^^^^^^^  
  File "/Users/frank/.local/share/uv/python/cpython-3.11.15-macos-aarch64-none/lib/python3.11/asyncio/runners.py", line 190, in run  
    return runner.run(main)  
           ^^^^^^^^^^^^^^^^  
  File "/Users/frank/.local/share/uv/python/cpython-3.11.15-macos-aarch64-none/lib/python3.11/asyncio/runners.py", line 118, in run  
    return self._loop.run_until_complete(task)  
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^  
  File "/Users/frank/.local/share/uv/python/cpython-3.11.15-macos-aarch64-none/lib/python3.11/asyncio/base_events.py", line 654, in run_until_complete  
    return future.result()  
           ^^^^^^^^^^^^^^^  
  File "/Users/frank/.hermes/hermes-agent/venv/lib/python3.11/site-packages/prompt_toolkit/application/application.py", line 886, in run_async  
    return await _run_async(f)  
           ^^^^^^^^^^^^^^^^^^^  
  File "/Users/frank/.hermes/hermes-agent/venv/lib/python3.11/site-packages/prompt_toolkit/application/application.py", line 734, in _run_async  
    with self.input.raw_mode(), self.input.attach(  
  File "/Users/frank/.local/share/uv/python/cpython-3.11.15-macos-aarch64-none/lib/python3.11/contextlib.py", line 137, in __enter__  
    return next(self.gen)  
           ^^^^^^^^^^^^^^  
  File "/Users/frank/.hermes/hermes-agent/venv/lib/python3.11/site-packages/prompt_toolkit/input/vt100.py", line 165, in _attached_input  
    loop.add_reader(fd, callback_wrapper)  
  File "/Users/frank/.local/share/uv/python/cpython-3.11.15-macos-aarch64-none/lib/python3.11/asyncio/selector_events.py", line 344, in add_reader  
    self._add_reader(fd, callback, *args)  
  File "/Users/frank/.local/share/uv/python/cpython-3.11.15-macos-aarch64-none/lib/python3.11/asyncio/selector_events.py", line 271, in _add_reader  
    self._selector.register(fd, selectors.EVENT_READ,  
  File "/Users/frank/.local/share/uv/python/cpython-3.11.15-macos-aarch64-none/lib/python3.11/selectors.py", line 523, in register  
    self._selector.control([kev], 0, 0)  
OSError: [Errno 22] Invalid argument  
frank@frankdeMacBook-Pro ~ %`
```

### 2. MAC终端解决办法

```
# 进入 hermes 的虚拟环境  
cd /Users/frank/.hermes/hermes-agent  
source venv/bin/activate  
​  
# 升级关键包  
pip install --upgrade "prompt-toolkit>=3.0.43"  
pip install --upgrade aiofiles  # 如果使用了的话  
​  
# 或者切换到 Python 3.12（对 macOS 兼容性更好）  
uv python install 3.12  
# 然后重新创建虚拟环境  
uv sync --python 3.12
```

## 2. Iterm2解决办法

### 1. 在iterm出现的问题如下

1. 代码
```
    
    1. 在mac的终端能运行 ，但是在iterm中出现问题如下：Initializing agent...  
        ────────────────────────────────────────  
        ​  
        ⚠️  API call failed (attempt 1/3): APIConnectionError  
           🔌 Provider: deepseek  Model: deepseek-v4-flash  
           🌐 Endpoint: https://api.deepseek.com/v1  
           📝 Error: Connection error.  
        ⏳ Retrying in 2.9s (attempt 1/3)...  
        ⚠️  API call failed (attempt 2/3): APIConnectionError  
           🔌 Provider: deepseek  Model: deepseek-v4-flash  
           🌐 Endpoint: https://api.deepseek.com/v1  
           📝 Error: Connection error.  
        ⏳ Retrying in 5.1s (attempt 2/3)...  
        ⚠️  API call failed (attempt 3/3): APIConnectionError  
           🔌 Provider: deepseek  Model: deepseek-v4-flash  
           🌐 Endpoint: https://api.deepseek.com/v1  
           📝 Error: Connection error.  
        🔁 Transient APIConnectionError on deepseek — rebuilt client, waiting 6s before one last primary attempt.  
        ⚠️  API call failed (attempt 1/3): APIConnectionError  
           🔌 Provider: deepseek  Model: deepseek-v4-flash  
           🌐 Endpoint: https://api.deepseek.com/v1  
           📝 Error: Connection error.  
        ⏳ Retrying in 2.3s (attempt 1/3)...  
        ⚠️  API call failed (attempt 2/3): APIConnectionError  
           🔌 Provider: deepseek  Model: deepseek-v4-flash  
           🌐 Endpoint: https://api.deepseek.com/v1  
           📝 Error: Connection error.  
        ⏳ Retrying in 4.3s (attempt 2/3)...  
        ⚠️  API call failed (attempt 3/3): APIConnectionError  
           🔌 Provider: deepseek  Model: deepseek-v4-flash  
           🌐 Endpoint: https://api.deepseek.com/v1  
           📝 Error: Connection error.  
        ⚠️ Max retries (3) exhausted — trying fallback...  
        ❌ API failed after 3 retries — Connection error.  
           💀 Final error: Connection error.
        
```

### 2.解决办法【因为代理出现了问题】

```
export HTTP_PROXY=http://127.0.0.1:7897  
export HTTPS_PROXY=http://127.0.0.1:7897  
hermes chat
```