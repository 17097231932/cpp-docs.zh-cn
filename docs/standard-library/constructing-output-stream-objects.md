---
description: 了解详细信息：构造输出流对象
title: 构造输出流对象
ms.date: 11/04/2016
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
ms.openlocfilehash: e730e4cb675b216fa56b5624feb69fadcd61400a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233638"
---
# <a name="constructing-output-stream-objects"></a>构造输出流对象

如果只使用预定义的 `cout`、`cerr` 或 `clog` 对象，则无需构造输出流。 必须为以下对象使用构造函数：

- [输出文件流构造函数](#vclrfoutputfilestreamconstructorsanchor1)

- [输出字符串流构造函数](#vclrfoutputstringstreamconstructorsanchor2)

## <a name="output-file-stream-constructors"></a><a name="vclrfoutputfilestreamconstructorsanchor1"></a> 输出文件流构造函数

可使用以下两种方式之一构造输出文件流：

- 使用默认的构造函数，然后调用 `open` 成员函数。

   ```cpp
   ofstream myFile; // Static or on the stack
   myFile.open("filename");

   ofstream* pmyFile = new ofstream; // On the heap
   pmyFile->open("filename");
   ```

- 在构造函数调用过程中指定文件名和模式标志。

   ```cpp
   ofstream myFile("filename", ios_base::out);
   ```

## <a name="output-string-stream-constructors"></a><a name="vclrfoutputstringstreamconstructorsanchor2"></a>输出字符串流构造函数

若要构造一个输出字符串流，可以按照以下方法使用 `ostringstream`：

```cpp
using namespace std;
// ...
ostringstream myString;
myString << "this is a test" << ends;

string sp = myString.str(); // Obtain string
cout << sp << endl;
```

`ends`“操控器”向字符串添加必要的终止 null 字符。

## <a name="see-also"></a>请参阅

[输出流](../standard-library/output-streams.md)
