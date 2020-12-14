---
description: 了解详细信息：链接器属性页
title: “链接器”属性页
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 308b5d27eda497f196479b063388c33d1c4eddc8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199423"
---
# <a name="linker-property-pages"></a>“链接器”属性页

以下属性位于 "**项目**  >  **属性**" "  >  **配置属性**" "  >  **链接器**" 下。 有关链接器的详细信息，请参阅 [CL 调用链接器](cl-invokes-the-linker.md) 和 [链接器选项](linker-options.md)。

## <a name="general-property-page"></a>"常规属性" 页

### <a name="output-file"></a>输出文件

[/Out](out-output-file-name.md)选项重写链接器创建的程序的默认名称和位置。

### <a name="show-progress"></a>显示进度

打印链接器进度消息

**选项**

- **未设置** -无详细级别。
- **显示所有进度消息** -显示所有进度消息。
- **对于搜索的库** -显示只指示所搜索的库的进度消息。
- **关于优化链接期间的 COMDAT 折叠** -显示有关优化链接期间的 COMDAT 折叠的信息。
- **关于优化链接期间移除的数据** -显示有关优化链接期间移除的函数和数据的信息。
- **关于与 SEH 不兼容的模块** -显示与安全异常处理不兼容的模块的信息。
- **关于与托管代码相关的链接器活动** -显示有关与托管代码相关的链接器活动的信息。

### <a name="version"></a>版本

[/VERSION](version-version-information.md)选项告知链接器将版本号置于 .exe 或 .dll 文件的标头中。 使用 DUMPBIN/HEADERS 查看可选标头值的 "图像版本" 字段，以查看 **/VERSION** 的效果。

### <a name="enable-incremental-linking"></a>启用增量链接

启用增量链接。  ([/INCREMENTAL](incremental-link-incrementally.md)，/INCREMENTAL： NO) 

### <a name="suppress-startup-banner"></a>取消显示启动版权标志

[/Nologo](nologo-suppress-startup-banner-linker.md)选项禁止显示版权消息和版本号。

### <a name="ignore-import-library"></a>Ignore Import Library

此属性指示链接器不要将基于该版本生成的任何 .lib 输出链接到任何相关项目。 它允许项目系统处理在生成时不生成 .lib 文件的 .dll 文件。 如果项目依赖于创建 DLL 的另一个项目，则项目系统会自动链接该子项目生成的 .lib 文件。 此属性可能在生成 COM Dll 或纯资源 Dll 的项目中不必要，因为这些 Dll 没有任何有意义的导出。 如果 DLL 没有导出，链接器不会生成 .lib 文件。 如果不存在导出 .lib 文件，并且项目系统通知链接器与缺少的 DLL 链接，链接将失败。 使用 Ignore Import Library 属性解决此问题。 当设置为 **"是"** 时，项目系统将忽略 .lib 文件是否存在，并使依赖于此项目的任何项目不与不存在的 .lib 文件链接。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>。

### <a name="register-output"></a>Register Output

在生成输出上运行 `regsvr32.exe /s $(TargetPath)`，仅在 .dll 项目上有效。 对于 .exe 项目，则忽略此属性。 要注册 .exe 输出，请在配置上设置生成后事件以执行注册 .exe 文件始终所需的自定义注册。

若要以编程方式访问此属性，请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>。

### <a name="per-user-redirection"></a>Per-user Redirection

传统上，Visual Studio 中的注册是在 HKEY_CLASSES_ROOT (HKCR) 中完成的。 如果使用 Windows Vista 及更高版本的操作系统，则必须在提升模式下运行 Visual Studio 才能访问 HKCR。 开发人员并不总是希望在提升模式下运行，但仍必须与注册一起工作。 每个用户的重定向允许注册，而无需在提升模式下运行。

Per-user Redirection 强制将任何对 HKCR 的写入重定向到 HKEY\_CURRENT\_USER (HKCU)。 如果关闭了 Per-user Redirection，当程序试图写入到 HKCR 时，可能导致[项目生成错误 PRJ0050](../../error-messages/tool-errors/project-build-error-prj0050.md)。

### <a name="additional-library-directories"></a>附加库目录

允许用户重写环境库路径。  ([/LIBPATH](libpath-additional-libpath.md)：文件夹) 

### <a name="link-library-dependencies"></a>链接库依赖项

指定是否链接由依赖项目生成的 .lib 文件。 通常，您需要在 .lib 文件中链接，但对于某些 Dll，可能不会出现这种情况。

也可通过提供文件名和相对路径来指定 .obj 文件，如“..\\..\MyLibProject\MyObjFile.obj”。 如果 .obj 文件的源代码 #includes 一个预编译标头（例如，.pch），则 pch 文件位于与 MyObjFile 相同的文件夹中。还必须添加 .pch 作为附加依赖项。

### <a name="use-library-dependency-inputs"></a>使用库依赖项输入

指定在项目依赖项的库输出中进行链接时，是否使用管理员工具的输入，而不是库文件本身。 在大型项目中，当依赖项目生成 .lib 文件时，将禁用增量链接。 如果有许多依赖项目生成 .lib 文件，则生成应用程序可能需要很长时间。 当此属性设置为 **"是"** 时，项目系统会链接依赖项目生成的 .lib 文件中的 .obj 文件，从而启用增量链接。

有关如何访问 " **常规** 链接器" 属性页的信息，请参阅 [在 Visual Studio 中设置 c + + 编译器和生成属性](../working-with-project-properties.md)。

### <a name="link-status"></a>链接状态

指定链接器是否应显示进度指示器以显示链接完成的百分比。 默认情况下，不显示此状态信息。  ([/ltcg](ltcg-link-time-code-generation.md)： STATUS |LTCG： NOSTATUS) 

### <a name="prevent-dll-binding"></a>阻止 DLL 绑定

[/ALLOWBIND](allowbind-prevent-dll-binding.md)： NO 在 DLL 的标头中设置一个位，指示 Bind.exe 不允许绑定该图像。 如果 DLL 已经进行数字签名（绑定使签名无效），可能不需要绑定 DLL。

### <a name="treat-linker-warning-as-errors"></a>将链接器警告视为错误

[/Wx](wx-treat-linker-warnings-as-errors.md) 导致在链接器生成警告时不生成任何输出文件。

### <a name="force-file-output"></a>强制文件输出

[/Force](force-force-file-output.md)选项通知链接器创建 .exe 文件或 DLL，即使引用的是符号但未定义或被多次定义。 它可能会创建无效的 .exe 文件。

**选项**

- **已启用** -不带参数的/force 表示多个和未解析。
- **仅限定义的符号** ，使用/FORCE： MULTIPLE 可创建输出文件，即使 LINK 找到符号的多个定义。
- **仅限未定义的符号** -使用/FORCE：无法解析以创建输出文件，而不管 LINK 是否找到未定义的符号。 /FORCE：如果入口点符号未解析，则忽略未解析的。

### <a name="create-hot-patchable-image"></a>创建热可修补映像

准备映像以进行热修补。

**选项**

- **已启用** -准备映像以进行热修补。
- **仅 X86 映像** -为热修补准备 X86 映像。
- **仅 X64 映像** -为热修补准备 X64 映像。
- **仅限 Itanium 映像** -为热修补准备 Itanium 映像。

### <a name="specify-section-attributes"></a>指定节特性

[/SECTION](section-specify-section-attributes.md)选项将更改节的特性，重写编译节的 .obj 文件时设置的特性。

## <a name="input-property-page"></a>输入属性页

### <a name="additional-dependencies"></a>附加依赖项

指定要添加到链接命令行的附加项，例如 *kernel32.dll*。

### <a name="ignore-all-default-libraries"></a>忽略所有默认库

[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)选项通知链接器从其在解析外部引用时搜索的库列表中删除一个或多个默认库。

### <a name="ignore-specific-default-libraries"></a>忽略特定默认库

指定一个或多个要忽略的默认库的名称。 用分号分隔多个库。  (/NODEFAULTLIB： [名称，名称，...]) 

### <a name="module-definition-file"></a>模块定义文件

[/DEF](def-specify-module-definition-file.md)选项将模块定义文件 () 传递到链接器。 仅可指定一个 .def 文件来链接。

### <a name="add-module-to-assembly"></a>向程序集添加模块

使用 [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md) 选项，可以将模块引用添加到程序集。 模块中的类型信息将不可用于添加了模块引用的程序集程序。 但是，模块中的类型信息将可用于引用该程序集的任何程序。

### <a name="embed-managed-resource-file"></a>嵌入托管资源文件

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) 将资源文件嵌入到输出文件中。

### <a name="force-symbol-references"></a>强制符号引用

[/INCLUDE](include-force-symbol-references.md)选项告知链接器将指定的符号添加到符号表中。

### <a name="delay-loaded-dlls"></a>延迟加载的 Dll

[/DELAYLOAD](delayload-delay-load-import.md)选项导致延迟加载 dll。 Dll 名称指定要延迟加载的 DLL。

### <a name="assembly-link-resource"></a>程序集链接资源

[/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)选项创建指向输出文件中 .NET Framework 资源的链接;资源文件不会放入输出文件中。

## <a name="manifest-file-property-page"></a>"清单文件" 属性页

### <a name="generate-manifest"></a>生成清单

[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md) 指定链接器应创建并行清单文件。

### <a name="manifest-file"></a>清单文件

[/MANIFESTFILE](manifestfile-name-manifest-file.md) 使你可以更改清单文件的默认名称。 清单文件的默认名称是附加了 .manifest 的文件名。

### <a name="additional-manifest-dependencies"></a>附加清单依赖项

通过[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) ，您可以指定将放置在清单文件的依赖项节中的特性。

### <a name="allow-isolation"></a>允许隔离

指定清单查找的行为。  ([/ALLOWISOLATION](allowisolation-manifest-lookup.md)： NO) 

### <a name="enable-user-account-control-uac"></a> (UAC) 启用用户帐户控制

指定是否启用用户帐户控制。   ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)，/MANIFESTUAC： NO) 

### <a name="uac-execution-level"></a>UAC 执行级别

指定在用用户帐户控制运行时为应用程序请求的执行级别。   (/MANIFESTUAC： level = [value] ) 

**选项**

- **asInvoker** -UAC 执行级别：作为调用程序。
- **highestAvailable** -UAC 执行级别：最高可用。
- **requireAdministrator** -UAC 执行级别：需要管理员。

### <a name="uac-bypass-ui-protection"></a>UAC 绕过 UI 保护

指定是否绕过桌面上其他窗口的用户界面保护级别。  仅对辅助功能应用程序将此属性设置为 "是"。   ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)： uiAccess = [true | false] ) 

## <a name="debugging-property-page"></a>“调试”属性页

### <a name="generate-debug-info"></a>生成调试信息

此选项可用于创建 .exe 文件或 DLL 的调试信息。

**选项**

- **No** -不生成任何调试信息。
- **生成调试信息** -创建完整的程序数据库 (PDB) 适用于分发到 Microsoft 符号服务器的理想选择。
- **为更快的链接生成调试信息优化** -生成程序数据库 (PDB) 适用于编辑-链接-调试循环的理想选择。
- **生成针对共享和发布进行了优化的调试信息** -生成程序数据库 (PDB) 理想的，以供编辑-链接-调试循环使用。

### <a name="generate-program-database-file"></a>生成程序数据库文件

默认情况下，当指定 [/debug](debug-generate-debug-info.md) 时，链接器会创建一个程序数据库 (PDB) 来保存调试信息。 PDB 的默认文件名具有程序的基名称和扩展名 .pdb。

### <a name="strip-private-symbols"></a>去除私有符号

使用生成 PDB 文件 (/DEBUG、/Z7、/Zd 或/Zi) 的任何编译器或链接器选项生成程序映像时， [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md) 选项将创建另一个程序数据库 (PDB) 文件。

### <a name="generate-map-file"></a>生成映射文件

[/MAP](map-generate-mapfile.md)选项告知链接器创建映射器。

### <a name="map-file-name"></a>映射文件名

用户指定的映射文件名。 它将替换默认名称。

### <a name="map-exports"></a>映射导出

[/MAPINFO](mapinfo-include-information-in-mapfile.md)选项告知链接器在映射器中包含指定的信息，如果指定了/MAP 选项，则会创建该映射。 导出通知链接器包含导出的函数。

### <a name="debuggable-assembly"></a>可调试程序集

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md) 发出带有调试信息跟踪的 DebuggableAttribute 特性并禁用 JIT 优化。

## <a name="system-property-page"></a>系统属性页

### <a name="subsystem"></a>SubSystem

[/SUBSYSTEM](subsystem-specify-subsystem.md)选项告知操作系统如何运行 .exe 文件。 子系统的选择会影响链接器将选择的入口点符号 (或入口点函数) 。

**选项**

- **未设置** -未设置子系统。
- **Console** -Win32 字符模式应用程序。 操作系统为控制台应用程序提供控制台。 如果定义了 main 或 wmain，则控制台为默认值。
- **Windows** 应用程序不需要控制台，这可能是因为它创建自己的 Windows 以便与用户交互。 如果定义了 WinMain 或 wWinMain，则默认情况下为 WINDOWS。
- Windows NT 的 **本机**-设备驱动程序。 如果指定了/DRIVER： WDM，则默认值为 NATIVE。
- **Efi 应用程序** -Efi 应用程序。
- **Efi 启动服务驱动** 程序-Efi 启动服务驱动程序。
- **EFI ROM** -EFI ROM。
- **Efi 运行时** -Efi 运行时。
- **Posix** -与 Windows NT 中的 posix 子系统一起运行的应用程序。

### <a name="minimum-required-version"></a>所需最低版本

指定子系统所需的最低版本。 参数是介于0到65535之间的十进制数字。

### <a name="heap-reserve-size"></a>堆保留大小

指定虚拟内存中堆分配的合计大小。 默认值为 1 MB。     ([/HEAP](heap-set-heap-size.md)：保留) 

### <a name="heap-commit-size"></a>堆提交大小

指定物理内存中堆分配的合计大小。 默认值为 4 KB。     ([/HEAP](heap-set-heap-size.md)： reserve、commit) 

### <a name="stack-reserve-size"></a>堆栈预留大小

指定虚拟内存中的堆栈分配总大小。 默认值为 1 MB。      ([/STACK](stack-stack-allocations.md)：保留) 

### <a name="stack-commit-size"></a>堆栈提交大小

指定物理内存中堆栈分配的合计大小。 默认值为 4 KB。      ([/STACK](stack-stack-allocations.md)： reserve、commit) 

### <a name="enable-large-addresses"></a>启用大地址

[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)选项告知链接器应用程序可以处理大于 2 gb 的地址。 默认情况下，如果未在链接器行上指定/LARGEADDRESSAWARE，则默认情况下启用/LARGEADDRESSAWARE： NO。

### <a name="terminal-server"></a>终端服务器

[/TSAWARE](tsaware-create-terminal-server-aware-application.md)选项在程序映像的可选标头的 IMAGE_OPTIONAL_HEADER DllCharacteristics 字段中设置标志。 当设置此标志后，终端服务器将不会向应用程序进行某些更改。

### <a name="swap-run-from-cd"></a>从 CD 交换运行

[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)选项告知操作系统首先将链接器输出复制到交换文件，然后从此处运行映像。 此选项是 Windows NT 4.0 (及更高版本) 功能。 指定 **CD** 后，操作系统会将可移动磁盘上的映像复制到页面文件，然后将其加载。

### <a name="swap-run-from-network"></a>从网络交换运行

[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)选项告知操作系统首先将链接器输出复制到交换文件，然后从此处运行映像。 此选项是 Windows NT 4.0 (及更高版本) 功能。 如果指定 **NET** ，则操作系统将首先将二进制映像从网络复制到交换文件，然后从该文件中加载它。 此选项可用于在网络上运行应用程序。

### <a name="driver"></a>驱动程序

使用 [/DRIVER](driver-windows-nt-kernel-mode-driver.md) 链接器选项可生成 Windows NT 内核模式驱动程序。

**选项**

- **未设置** -默认驱动程序设置。
- **驱动** 程序-驱动程序
- **UP** /DRIVER： UPONLY 会导致链接器将 IMAGE_FILE_UP_SYSTEM_ONLY 位添加到 output 标头中的特性，以指定其为单处理器 () 驱动程序。 操作系统将拒绝在多处理器 (MP) 系统上加载 UP 驱动程序。
- **Wdm** -/DRIVER： wdm 使链接器在可选标头的 DLLCHARACTERISTICS 字段中设置 IMAGE_DLLCHARACTERISTICS_WDM_DRIVER 位。

## <a name="optimization-property-page"></a>"优化" 属性页

### <a name="references"></a>参考资料

[/Opt](opt-optimizations.md)： REF 消除了在/opt 时从不引用的函数和/或数据： NOREF 保留从未引用的函数和/或数据。

### <a name="enable-comdat-folding"></a>启用 COMDAT 折叠

使用 [/opt](opt-optimizations.md)： ICF \[ = 迭代] 执行相同的 COMDAT 折叠。

### <a name="function-order"></a>函数顺序

[/Order](order-put-functions-in-order.md)选项通过以预先确定的顺序将特定的 comdat 放入图像，告诉链接优化程序。 LINK 按指定顺序将函数置于图像的每个部分中。

### <a name="profile-guided-database"></a>按配置文件数据库

为按配置文件优化指定 .pgd 文件。  ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md)) 

### <a name="link-time-code-generation"></a>链接时间代码生成

指定链接时间代码生成。  ([/ltcg](ltcg-link-time-code-generation.md)) 

**选项**

- **默认** 值-默认 LTCG 设置。
- **使用快速链接时间代码生成** -使用 [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)的链接时间代码生成。
- **使用链接时间代码生成** -使用 [链接时间代码生成](ltcg-link-time-code-generation.md)。
- **按配置优化-检测** -将 [按配置](../profile-guided-optimizations.md) 优化使用:P ginstrument。
- **按配置优化** -指定链接器应使用在运行检测的二进制文件后创建的配置文件数据来创建优化的映像。
- **按配置优化-更新** -允许和跟踪从:P ginstrument 阶段指定的内容添加或修改的输入文件列表。

## <a name="embedded-idl-property-page"></a>Embedded IDL 属性页

### <a name="midl-commands"></a>MIDL 命令

指定 MIDL 命令行选项。  ([/MIDL](midl-specify-midl-command-line-options.md) :@responsefile) 

### <a name="ignore-embedded-idl"></a>忽略嵌入的 IDL

[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)选项指定不应将源代码中的任何 IDL 特性处理到 .idl 文件中。

### <a name="merged-idl-base-file-name"></a>合并的 IDL 基文件名

[/IDLOUT](idlout-name-midl-output-files.md)选项指定 .idl 文件的名称和扩展名。

### <a name="type-library"></a>类型库

[/TLBOUT](tlbout-name-dot-tlb-file.md)选项指定 .tlb 文件的名称和扩展名。

### <a name="typelib-resource-id"></a>TypeLib 资源 ID

允许您指定链接器生成的类型库的资源 ID。  ([/TLBID](tlbid-specify-resource-id-for-typelib.md)： id) 

## <a name="windows-metadata-property-page"></a>"Windows 元数据" 属性页

### <a name="generate-windows-metadata"></a>生成 Windows 元数据

启用或禁用 Windows 元数据的生成。

**选项**

- **是** -启用 Windows 元数据文件的生成。
- **否** -禁用 Windows 元数据文件的生成。

### <a name="windows-metadata-file"></a>Windows 元数据文件

[/WINMDFILE](winmdfile-specify-winmd-file.md)选项开关。

### <a name="windows-metadata-key-file"></a>Windows 元数据密钥文件

指定密钥或密钥对来对 Windows 元数据进行签名。  ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md)： filename) 

### <a name="windows-metadata-key-container"></a>Windows 元数据密钥容器

指定用于对 Windows 元数据进行签名的密钥容器。  ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md)： name) 

### <a name="windows-metadata-delay-sign"></a>Windows 元数据延迟签名

对 Windows 元数据进行部分签名。 如果只希望将公钥放在 Windows 元数据中，请使用 [/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md) 。 默认值为/WINMDDELAYSIGN： NO。

## <a name="advanced-property-page"></a>"高级" 属性页

### <a name="entry-point"></a>入口点

[/ENTRY](entry-entry-point-symbol.md)选项将入口点函数指定为 .exe 文件或 DLL 的起始地址。

### <a name="no-entry-point"></a>无入口点

[/NOENTRY](noentry-no-entry-point.md)选项是创建纯资源 dll 所必需的。使用此选项可防止链接将引用链接到 `_main` DLL。

### <a name="set-checksum"></a>设置校验和

[/RELEASE](release-set-the-checksum.md)选项在 .exe 文件的标头中设置校验和。

### <a name="base-address"></a>基址

为程序设置基址。  ([/base](base-base-address.md)： {address \[ ，size] | @filename ，key} ) 

### <a name="randomized-base-address"></a>随机基址

随机基址。  ([/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) \[ ： NO] ) 

### <a name="fixed-base-address"></a>固定基址

创建只能在其首选基址加载的程序。  ([/FIXED](fixed-fixed-base-address.md) \[ ： NO] ) 

### <a name="data-execution-prevention-dep"></a>数据执行保护 (DEP)

将可执行文件标记为经过测试，以与 Windows 数据执行保护功能兼容。  ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md) \[ ： NO] ) 

### <a name="turn-off-assembly-generation"></a>关闭程序集生成

[/NOASSEMBLY](noassembly-create-a-msil-module.md)选项告知链接器创建当前输出文件的映像，而不包含 .NET Framework 的程序集。

### <a name="unload-delay-loaded-dll"></a>卸载延迟加载的 DLL

**卸载** 限定符告知延迟加载 helper 函数支持 DLL 的显式卸载。  ([/DELAY](delay-delay-load-import-settings.md)：卸载) 

### <a name="nobind-delay-loaded-dll"></a>Nobind 延迟加载的 DLL

**NOBIND** 限定符通知链接器不要在最终映像中包含可绑定的 IAT。 默认值是为延迟加载的 DLL 创建可绑定的 IAT。  ([/DELAY](delay-delay-load-import-settings.md)： NOBIND) 

### <a name="import-library"></a>导入库

重写默认的导入库名。  ([/IMPLIB](implib-name-import-library.md)： filename) 

### <a name="merge-sections"></a>合并部分

[/Merge](merge-combine-sections.md)选项将第一节 (从) ，第二部分结合 (到) ，并将生成的部分命名为。 例如，/merge：. rdata =。

### <a name="target-machine"></a>目标计算机

[/MACHINE](machine-specify-target-platform.md)选项指定程序的目标平台。

**选项**

- **未设置**
- **MachineARM**
- **MachineARM64**
- **MachineEBC**
- **MachineIA64**
- **MachineMIPS**
- **MachineMIPS16**
- **MachineMIPSFPU**
- **MachineMIPSFPU16**
- **MachineSH4**
- **MachineTHUMB**
- **MachineX64**
- **MachineX86**

### <a name="profile"></a>配置文件

生成一个可与“性能工具”探查器结合使用的输出文件。 需要设置 GenerateDebugInformation (/[/debug](debug-generate-debug-info.md)) 。  ([/PROFILE](profile-performance-tools-profiler.md)) 

### <a name="clr-thread-attribute"></a>CLR 线程特性

显式指定 CLR 程序入口点的线程特性。

**选项**

- **MTA 线程特性** -将 MTAThreadAttribute 特性应用于程序的入口点。
- **STA 线程特性** -将 STAThreadAttribute 特性应用于程序的入口点。
- **默认线程属性** -与未指定 [/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)的属性相同。 使公共语言运行时 (CLR) 设置默认线程特性。

### <a name="clr-image-type"></a>CLR 映像类型

设置 CLR 映像的类型（IJW、纯或安全）。

**选项**

- **强制 IJW 映像**
- **强制纯 IL 映像**
- **强制安全 IL 映像**
- **默认图像类型**

### <a name="key-file"></a>密钥文件

指定密钥或密钥对以对程序集进行签名。  ([/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)： filename) 

### <a name="key-container"></a>密钥容器

指定用于对程序集进行签名的密钥容器。  ([/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)： name) 

### <a name="delay-sign"></a>延迟签名

对程序集进行部分签名。 如果只希望将公钥放入程序集中，请使用 [/DELAYSIGN](delaysign-partially-sign-an-assembly.md) 。 默认值为/DELAYSIGN： NO。

### <a name="clr-unmanaged-code-check"></a>CLR 非托管代码检查

[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md) 指定链接器是否将 SuppressUnmanagedCodeSecurityAttribute 应用到链接器生成的从托管代码到本机 Dll 的 PInvoke 调用。

### <a name="error-reporting"></a>错误报告

允许您直接向 Visual C++ 团队提供内部编译器错误(ICE)信息。

**选项**

- **PromptImmediately** -立即提示。
- 下一次登录时 **队列，** 用于下一次登录。
- **发送错误报告** -发送错误报告。
- **无错误报告** -无错误报告。

### <a name="sectionalignment"></a>SectionAlignment

[/Align](align-section-alignment.md)选项指定程序的线性地址空间内每个部分的对齐方式。 Number 参数以字节为单位，必须是2的幂。

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>保留 PInvoke 调用的最后一个错误代码

默认情况下， [/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)将保留通过 P/Invoke 机制调用的函数的最后一个错误代码，该机制允许您通过用/clr 编译的代码调用 dll 中的本机函数。

**选项**

- **Enabled** -Enable CLRSupportLastError。
- **Disabled** -禁用 CLRSupportLastError。
- **仅限系统 dll** -仅为系统 Dll 启用 CLRSupportLastError。

### <a name="image-has-safe-exception-handlers"></a>映像具有安全异常处理程序

当指定了 [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) 时，链接器将仅生成一个图像，如果它还可以生成一个映像的安全异常处理程序表。 此表指定操作系统的哪些异常处理程序对图像有效。
