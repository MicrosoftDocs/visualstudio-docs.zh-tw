---
title: 自訂 VSTU 所建立的專案檔 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
caps.latest.revision: 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: ef11a6585d741fd28de918d4fa2a81f1eb927b43
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47484956"
---
# <a name="customize-project-files-created-by-vstu"></a>自訂 VSTU 所建立的專案檔
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[來自訂專案檔案 VSTU 所建立的](https://docs.microsoft.com/visualstudio/cross-platform/customize-project-files-created-by-vstu)。  
  
  
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
  
## <a name="see-also"></a>另請參閱  
 [範例：記錄回呼](../cross-platform/share-the-unity-log-callback-with-vstu.md)

