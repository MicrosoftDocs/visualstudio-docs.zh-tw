---
title: 與 VSTU 共用 Unity 記錄回呼 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d71f906-6e50-4399-b59b-d38c6dfef7ee
caps.latest.revision: 5
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: 278258d50f82fc55e26caf51d5989b2a7c4583fb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758462"
---
# <a name="share-the-unity-log-callback-with-vstu"></a>與 VSTU 共用 Unity 記錄回呼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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

