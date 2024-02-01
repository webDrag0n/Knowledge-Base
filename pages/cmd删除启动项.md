- #Windows #cmd #启动项
- Windows cmd删除启动项的方法，踩了好多坑终于找到了
- 参考：https://blog.walterlv.com/post/cmd-startup-arguments.html
- ```
  HKEY_LOCAL_MACHINE\Software\Microsoft\Command Processor\AutoRun
  - 和/或
  - HKEY_CURRENT_USER\Software\Microsoft\Command Processor\AutoRun
  ```
- 命令扩展是按默认值启用的。你也可以使用 /E:OFF ，为某一 特定调用而停用扩展。你 可以在机器上和/或用户登录会话上 启用或停用 CMD.EXE 所有调用的扩展，这要通过设置使用 REGEDIT.EXE 的注册表中的一个或两个 REG_DWORD 值:
- |  |
- ```
  HKEY_LOCAL_MACHINE\Software\Microsoft\Command Processor\EnableExtensions
  - 和/或
  - HKEY_CURRENT_USER\Software\Microsoft\Command Processor\EnableExtensions
  ```
- |
- 到 0x1 或 0x0。用户特定设置 比机器设置有优先权。命令行 开关比注册表设置有优先权。
- 在批处理文件中，SETLOCAL ENABLEEXTENSIONS 或 DISABLEEXTENSIONS 参数 比 /E:ON 或 /E:OFF 开关有优先权。请参阅 SETLOCAL /? 获取详细信息。
- 命令扩展包括对下列命令所做的 更改和/或添加:
- |  |
- ```
  DEL or ERASE
  COLOR
  CD or CHDIR
  MD or MKDIR
  PROMPT
  PUSHD
  POPD
  SET
  SETLOCAL
  ENDLOCAL
  IF
  FOR
  CALL
  SHIFT
  GOTO
  START (同时包括对外部命令调用所做的更改)
  ASSOC
  FTYPE
  ```
- |
- 有关特定详细信息，请键入 commandname /? 查看。
- 延迟环境变量扩展不按默认值启用。你 可以用/V:ON 或 /V:OFF 开关，为 CMD.EXE 的某个调用而 启用或停用延迟环境变量扩展。你 可以在机器上和/或用户登录会话上启用或停用 CMD.EXE 所有 调用的延迟扩展，这要通过设置使用 REGEDIT.EXE 的注册表中的 一个或两个 REG_DWORD 值:
- |  |
- ```
  HKEY_LOCAL_MACHINE\Software\Microsoft\Command Processor\DelayedExpansion
  - 和/或
  - HKEY_CURRENT_USER\Software\Microsoft\Command Processor\DelayedExpansion
  ```
- 到 0x1 或 0x0。用户特定设置 比机器设置有优先权。命令行开关 比注册表设置有优先权。
- 在批处理文件中，SETLOCAL ENABLEDELAYEDEXPANSION 或 DISABLEDELAYEDEXPANSION 参数比 /V:ON 或 /V:OFF 开关有优先权。请参阅 SETLOCAL /? 获取详细信息。
- 如果延迟环境变量扩展被启用， 惊叹号字符可在执行时间被用来 代替一个环境变量的数值。
- 你可以用 /F:ON 或 /F:OFF 开关为 CMD.EXE 的某个 调用而启用或禁用文件名完成。你可以在计算上和/或 用户登录会话上启用或禁用 CMD.EXE 所有调用的完成， 这可以通过使用 REGEDIT.EXE 设置注册表中的下列 REG_DWORD 的全部或其中之一:
- |  |
- ```
  HKEY_LOCAL_MACHINE\Software\Microsoft\Command Processor\CompletionChar
  HKEY_LOCAL_MACHINE\Software\Microsoft\Command Processor\PathCompletionChar
  - 和/或
  - HKEY_CURRENT_USER\Software\Microsoft\Command Processor\CompletionChar
  HKEY_CURRENT_USER\Software\Microsoft\Command Processor\PathCompletionChar
  ```
- 由一个控制字符的十六进制值作为一个特定参数(例如，0x4 是Ctrl-D，0x6 是 Ctrl-F)。用户特定设置优先于机器设置。 命令行开关优先于注册表设置。
- 如果完成是用 /F:ON 开关启用的，两个要使用的控制符是: 目录名完成用 Ctrl-D，文件名完成用 Ctrl-F。要停用 注册表中的某个字符，请用空格(0x20)的数值，因为此字符 不是控制字符。
- 如果键入两个控制字符中的一个，完成会被调用。完成功能将 路径字符串带到光标的左边，如果没有通配符，将通配符附加 到左边，并建立相符的路径列表。然后，显示第一个相符的路 径。如果没有相符的路径，则发出嘟嘟声，不影响显示。之后， 重复按同一个控制字符会循环显示相符路径的列表。将 Shift 键跟控制字符同时按下，会倒着显示列表。如果对该行进行了 任何编辑，并再次按下控制字符，保存的相符路径的列表会被 丢弃，新的会被生成。如果在文件和目录名完成之间切换，会 发生同样现象。两个控制字符之间的唯一区别是文件完成字符 符合文件和目录名，而目录完成字符只符合目录名。如果文件 完成被用于内置式目录命令(CD、MD 或 RD)，就会使用目录 完成。 用引号将相符路径括起来，完成代码可以正确处理含有空格 或其他特殊字符的文件名。同时，如果备份，然后从行内调用 文件完成，完成被调用时位于光标右方的文字会被调用。
- 需要引号的特殊字符是: `<space>` `()[]{}^=;!'+,`~(&()`