---
title: XslTransformation 工作 | Microsoft Docs
description: 瞭解 MSBuild 如何使用 XslTransformation 工作，將使用 XSLT 和輸出的 XML 輸入轉換成輸出裝置或檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f779fc5d222fdd0985adef203f0bb20fc601a429
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847942"
---
# <a name="xsltransformation-task"></a>XslTransformation 工作

使用 XSLT 或已編譯的 XSLT 來轉換 XML 輸入，並輸出到輸出裝置或檔案。

## <a name="parameters"></a>參數

 下表說明 `XslTransformation` 工作的參數。

|參數|Description|
|---------------|-----------------|
|`OutputPaths`|必要的 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定 XML 轉換的輸出檔案。|
|`Parameters`|選擇性的 `String` 參數。<br /><br /> 指定「XSLT 輸入」文件的參數。  提供保存每個參數的原始 XML `<Parameter Name="" Value="" Namespace="" />` 。|
|`XmlContent`|選擇性的 `String` 參數。<br /><br /> 以字串形式指定 XML 輸入。|
|`XmlInputPaths`|選擇性 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 參數。<br /><br /> 指定 XML 輸入檔案。|
|`XslCompiledDllPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定已編譯的 XSLT。|
|`XslContent`|選擇性的 `String` 參數。<br /><br /> 以字串形式指定 XSLT 輸入。|
|`XslInputPath`|選擇性的 <xref:Microsoft.Build.Framework.ITaskItem> 參數。<br /><br /> 指定 XSLT 輸入檔案。|

## <a name="remarks"></a>備註

 除了具有表格中所列的參數之外，此工作也繼承 <xref:Microsoft.Build.Tasks.TaskExtension> 類別的參數，而該類別本身又繼承 <xref:Microsoft.Build.Utilities.Task> 類別。 如需這些額外參數的清單及其描述，請參閱 [TaskExtension 基類（base class](../msbuild/taskextension-base-class.md)）。

## <a name="example"></a>範例

在下列範例中，會使用 XSL 轉換檔案 *轉換。 xslt* 是用來修改 xml 檔案 `$(XmlInputFileName)` 。 轉換的 XML 會寫入至 `$(IntermediateOutputPath)output.xml` 。 XSL 轉換採用 `$(Parameter1)` 做為輸入參數。

```xml
    <XslTransformation XslInputPath="transform.xslt"
                       XmlInputPaths="$(XmlInputFileName)"
                       OutputPaths="$(IntermediateOutputPath)output.xml"
                       Parameters="&lt;Parameter Name='Parameter1' Value='$(Parameter1)'/&gt;"/>
```

## <a name="see-also"></a>另請參閱

- [XSLT 參數](/dotnet/standard/data/xml/xslt-parameters)
- [工作](../msbuild/msbuild-tasks.md)
- [工作參考](../msbuild/msbuild-task-reference.md)
