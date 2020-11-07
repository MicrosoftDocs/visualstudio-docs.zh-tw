---
title: 自訂 VSTU 所建立的專案檔 | Microsoft Docs
description: '瞭解如何自訂 Visual Studio Tools for Unity (VSTU) 所建立的專案檔。 查看 c # 程式碼範例。'
ms.custom: ''
ms.date: 07/26/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 071dc7a9f12dcfeb5fff9e59bbbf34dc64f61cf5
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341568"
---
# <a name="customize-project-files-created-by-vstu"></a>自訂 VSTU 所建立的專案檔
Visual Studio Tools for Unity 在專案檔產生期間提供 Unity 樣式回呼。 使用 `VisualStudioIntegration.ProjectFileGeneration` 事件註冊可在每次重新產生時修改專案檔。

## <a name="demonstrates"></a>示範
 如何自訂 Visual Studio Tools for Unity 所產生的 Visual Studio 專案檔。

## <a name="example"></a>範例

```csharp
#if ENABLE_VSTU
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
#endif
```

## <a name="see-also"></a>另請參閱
 [範例：記錄回呼](/cross-platform/share-the-unity-log-callback-with-vstu.md)
