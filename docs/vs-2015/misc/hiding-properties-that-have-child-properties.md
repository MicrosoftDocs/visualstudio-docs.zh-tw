---
title: 隱藏具有子屬性的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: 76ef9c093bb91bc3cc22df7b56c4d5d69dbc41a5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196517"
---
# <a name="hiding-properties-that-have-child-properties"></a>隱藏具有子屬性的屬性
您會想要隱藏具有子屬性的屬性：  
  
-   如果您有巢狀的專案父專案以程式設計方式控制子專案的某些層面。  
  
-   如果您使用控制項與特製化的設計工具，而且不想讓開發人員控制項的所有屬性的完整存取權。  
  
-   如果您有範圍的物件擁有權，而且想要的檢視內容限制。  
  
### <a name="to-hide-properties-that-have-child-properties"></a>若要隱藏具有子屬性的屬性  
  
1.  設定`pfDisplay`中的參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A>至`FALSE`。  
  
2.  設定`pfHide`中的參數<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>至`TRUE`。  
  
## <a name="see-also"></a>另請參閱  
 [屬性顯示格線](../extensibility/internals/properties-display-grid.md)