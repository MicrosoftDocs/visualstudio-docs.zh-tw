---
title: 隱藏具有子屬性的屬性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d20b865c6f07d76320a7df8402810c82869ddfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822382"
---
# <a name="hiding-properties-that-have-child-properties"></a>隱藏具有子屬性的屬性
您會想要隱藏具有子屬性的屬性：  
  
- 如果您有父專案以程式設計方式控制子專案某些方面的嵌套專案。  
  
- 如果您將控制項與特製化設計工具搭配使用，而您不想讓開發人員擁有控制項所有屬性的完整存取權。  
  
- 如果您有物件的範圍擁有權，而且想要限制屬性的顯示。  
  
### <a name="to-hide-properties-that-have-child-properties"></a>隱藏具有子屬性的屬性  
  
1. 將 `pfDisplay` 參數設定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> 為 `FALSE` 。  
  
2. 將 `pfHide` 參數設定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> 為 `TRUE` 。  
  
## <a name="see-also"></a>另請參閱  
 [屬性顯示格線](../extensibility/internals/properties-display-grid.md)