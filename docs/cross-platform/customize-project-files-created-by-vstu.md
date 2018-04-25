---
title: 自訂 VSTU 所建立的專案檔 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 7393d023b8c581b95d3ac39b8501ca9dbb30228d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="customize-project-files-created-by-vstu"></a>自訂 VSTU 所建立的專案檔
Visual Studio Tools for Unity 在專案檔產生期間提供 Unity 樣式回呼。 使用 `VisualStudioIntegration.ProjectFileGeneration` 事件註冊可在每次重新產生時修改專案檔。

## <a name="demonstrates"></a>示範
 如何自訂 Visual Studio Tools for Unity 所產生的 Visual Studio 專案檔。

## <a name="example"></a>範例

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text;
using System.Xml.Linq;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class ProjectFileHook
{
    // necessary for XLinq to save the xml project file in utf8
    class Utf8StringWriter : StringWriter
    {
        public override Encoding Encoding
        {
            get { return Encoding.UTF8; }
        }
    }

    static ProjectFileHook()
    {
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>
        {
            // parse the document and make some changes
            var document = XDocument.Parse(content);
            document.Root.Add(new XComment("FIX ME"));

            // save the changes using the Utf8StringWriter
            var str = new Utf8StringWriter();
            document.Save(str);

            return str.ToString();
        };
    }
}
```

## <a name="see-also"></a>請參閱
 [範例：記錄回呼](../cross-platform/share-the-unity-log-callback-with-vstu.md)
