---
title: "與 VSTU 共用 Unity 記錄回呼 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: "2"
author: conceptdev
ms.author: crdun
manager: crdun
ms.openlocfilehash: 7aae3c7bc11cdde209ef4d663793f25fa1e9e67e
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/29/2017
---
# <a name="share-the-unity-log-callback-with-vstu"></a>與 VSTU 共用 Unity 記錄回呼
Visual Studio Tools for Unity 使用 Unity 註冊記錄回呼，以便將其主控台串流至 Visual Studio。 如果您的編輯器指令碼也使用 Unity 註冊記錄回呼，VSTU 回呼可能會與您的回呼相衝突。 若要避免這種可能性，請使用 `VisualStudioIntegration.LogCallback` 事件來與 VSTU 合作。  

## <a name="demonstrates"></a>示範  
 如何共用 Visual Studio Tools for Unity 所建立的 Unity 記錄回呼。  

## <a name="example"></a>範例  

```csharp  
using System;  

using UnityEngine;  
using UnityEditor;  

using SyntaxTree.VisualStudio.Unity.Bridge;  

[InitializeOnLoad]  
public class LogCallbackHook  
{  
    static LogCallbackHook()  
    {  
        VisualStudioIntegration.LogCallback += (string condition, string trace, LogType type) =>  
        {  
            // place code that implements your log callback here  
        };  
    }  
}  
```  

## <a name="see-also"></a>另請參閱  
 [範例：產生專案檔](../cross-platform/customize-project-files-created-by-vstu.md)
