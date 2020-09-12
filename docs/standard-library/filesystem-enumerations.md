---
title: '&lt;filesystem&gt; 枚举'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::filesystem::copy_options
- filesystem/std::experimental::filesystem::copy_options
- filesystem/std::filesystem::directory_options
- filesystem/std::experimental::filesystem::directory_options
- filesystem/std::filesystem::file_type
- filesystem/std::experimental::filesystem::file_type
- filesystem/std::filesystem::perms
- filesystem/std::experimental::filesystem::perms
ms.assetid: 0096c046-d101-464c-8259-b878a48280b0
ms.openlocfilehash: 3c94ec899f0ea7abf71530f6aca44638fdb216c9
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041934"
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;filesystem&gt; 枚举

本主题介绍文件系统标头中的枚举。

## <a name="requirements"></a>要求

**标头：**\<experimental/filesystem>

**命名空间：** std::experimental::filesystem

## <a name="copy_options"></a><a name="copy_options"></a> copy_options

和 [copy](filesystem-functions.md#copy) 和 [copy_file](filesystem-functions.md#copy_file) 函数一起用于指定行为的位掩码值的枚举。

### <a name="syntax"></a>语法

```cpp
enum class copy_options {
   none = 0,
   skip_existing = 1,
   overwrite_existing = 2,
   update_existing = 4,
   recursive = 8,
   copy_symlinks = 16,
   skip_symlinks = 32,
   directories_only = 64,
   create_symlinks = 128,
   create_hard_links = 256
};
```

### <a name="values"></a>值

| 名称 | 说明 |
|------------|-----------------|
|`none`|执行操作的默认行为。|
|`skip_existing`|在文件已存在时不复制，不报告错误。|
|`overwrite_existing`|在文件已存在时覆盖它。|
|`update_existing`|在文件已存在且时间早于替换文件时覆盖它。|
|`recursive`|以递归方式复制子目录及其内容。|
|`copy_symlinks`|将符号链接复制为符号链接，而非复制它们指向的文件。|
|`skip_symlinks`|忽略符号链接。|
|`directories_only`|仅循环访问目录，忽略文件。|
|`create_symlinks`|生成符号链接，而非复制文件。 必须将绝对路径用作源路径，除非目标是当前目录。|
|`create_hard_links`|生成硬链接，而非复制文件。|

## <a name="directory_options"></a><a name="directory_options"></a> directory_options

指定是跟踪指向目录的符号链接还是忽略它们。

### <a name="syntax"></a>语法

```cpp
enum class directory_options {
   none = 0,
   follow_directory_symlink
};
```

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`none`|默认行为：忽略指向目录的符号链接。 拒绝权限是错误。|
|`follow_directory_symlink`|将指向目录的符号链接视为实际目录。|

## <a name="file_type"></a><a name="file_type"></a> file_type

文件类型的枚举。 支持的值为 regular、directory、not_found 和 unknown。

### <a name="syntax"></a>语法

```cpp
enum class file_type {
    not_found = -1,
    none,
    regular,
    directory,
    symlink,
    block,
    character,
    fifo,
    socket,
    unknown
};
```

### <a name="values"></a>值

|名称|值|说明|
|----------|-----------|-----------------|
|`not_found`|-1|表示一个不存在的文件。|
|`none`|0|表示一个不具有类型特性的文件。 （不支持。）|
|`regular`|1|表示常规磁盘文件。|
|`directory`|2|表示一个目录。|
|`symlink`|3|表示一个符号链接。 （不支持。）|
|`block`|4|表示基于 UNIX 的系统上的块特殊文件。 （不支持。）|
|`character`|5|表示基于 UNIX 的系统上的字符特殊文件。 （不支持。）|
|`fifo`|6|表示基于 UNIX 的系统上的 FIFO 文件。 （不支持。）|
|`socket`|7|表示基于 UNIX 的系统上的套接字。 （不支持。）|
|`unknown`|8|表示状态无法确定的文件。|

## <a name="perm_options"></a><a name="perm_options"></a> perm_options

包括值 `replace` 、 `add` 、 `remove` 和 `nofollow` 。

```cpp
enum class perm_options;
```

## <a name="perms"></a><a name="perms"></a> perms

文件权限的标志。 支持的值实质上是 "readonly" 和 all。 对于只读文件，未设置任何 *_write 位。 其他文件设置了 `all` 位 (0x0777)。

### <a name="syntax"></a>语法

```cpp
enum class perms {// names for permissions
   none = 0,
   owner_read = 0400,  // S_IRUSR
   owner_write = 0200, // S_IWUSR
   owner_exec = 0100,  // S_IXUSR
   owner_all = 0700,   // S_IRWXU
   group_read = 040,   // S_IRGRP
   group_write = 020,  // S_IWGRP
   group_exec = 010,   // S_IXGRP
   group_all = 070,    // S_IRWXG
   others_read = 04,   // S_IROTH
   others_write = 02,  // S_IWOTH
   others_exec = 01,   // S_IXOTH
   others_all = 07,    // S_IRWXO
   all = 0777,
   set_uid = 04000,    // S_ISUID
   set_gid = 02000,    // S_ISGID
   sticky_bit = 01000, // S_ISVTX
   mask = 07777,
   unknown = 0xFFFF,
   add_perms = 0x10000,
   remove_perms = 0x20000,
   resolve_symlinks = 0x40000
};
```

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)
