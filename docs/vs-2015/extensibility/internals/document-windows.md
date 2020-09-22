---
title: 文件視窗 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, document windows
ms.assetid: 50081d48-987f-43db-8bf9-51b7cf76e9c0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e62be456422b7ee5e9f2828a44a6be05e1211d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838859"
---
# <a name="document-windows"></a>文件視窗
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在 Visual Studio 中， *文件視窗* 是與多重文件介面（ (MDI) 視窗）相關聯的框架子視窗。 文件視窗通常是用來顯示和修改原始程式碼或文字，但也可以裝載其他功能類型。 文件視窗：  
  
- 可以在父 MDI 的不同水準或垂直索引標籤群組中組織，如此一來，就可以同時查看多個檔案。  
  
- 可以停駐在父 MDI 的任何順序中。  
  
- 可以自由浮動。  
  
- 會以定位順序連結到其他 MDI 視窗。  
  
  您可以在 [文件視窗] 索引標籤的快捷方式功能表上，找到群組、停駐和浮動的命令。  
  
  如需 Visual Studio 中視窗行為的詳細資訊，請參閱 [自訂視窗版面](../../ide/customizing-window-layouts-in-visual-studio.md)配置。  
  
## <a name="document-window-implementation"></a>檔視窗執行  
 檔視窗是藉由執行編輯器來建立。 介面會在具現 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 化編輯器的過程中建立文件視窗。 如需詳細資訊，請參閱 [編輯器中的舊版介面](../../extensibility/legacy-interfaces-in-the-editor.md)。  
  
> [!NOTE]
> 若要在視窗中提供反向和向前導覽點，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBackForwardNavigation> 介面。 文字編輯器會使用文字標記來識別檔中的導覽點。  
  
## <a name="the-running-document-table"></a>執行中的檔資料表  
 IDE 會使用執行中的檔資料表 (RDT) 來追蹤每個文件視窗的狀態。 RDT 是一種機制，可讓文件視窗收到事件的通知，例如當關閉方案時，或是在編輯檔案時。 如需詳細資訊，請參閱執行 [檔資料表](../../extensibility/internals/running-document-table.md)。  
  
## <a name="see-also"></a>另請參閱  
 [已延遲載入文件](../../extensibility/internals/delayed-document-loading.md)
