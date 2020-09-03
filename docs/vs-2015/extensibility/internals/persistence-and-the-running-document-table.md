---
title: 持續性與執行中的檔資料表 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c422ad1735312c82c8dc027c4adf73c1b033685
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196089"
---
# <a name="persistence-and-the-running-document-table"></a>持續性與執行中的文件資料表
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

在 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 中，專案會完全負責管理其專案專案的持續性，而這些專案專案是使用服務來完成 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> 。 檔是 Visual Studio 環境中的基本持續性單位。 專案會協調檔的開啟、儲存和重新命名，以及執行中的檔資料表 (RDT) ，此資源會追蹤所有開啟檔的狀態。  
  
## <a name="managing-persistence"></a>管理持續性  
 專案會藉由執行介面來控制環境的持續性服務 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 。 雖然環境永遠不會直接要求檔保存，但是它會要求擁有專案 (或階層) 儲存檔。 如此一來，專案就可以將專案專案資料儲存至本機檔案、遠端檔案、資料庫、儲存機制或其他媒體。  
  
 全域環境會維護 RDT。 環境會維護 RDT 中所有開啟的視窗和檔的專案，讓他們可以接收特殊通知，例如關閉方案時。 此外，RDT 可讓環境在 **方案總管**中追蹤對應的節點。 RDT 會維護每個 open、永久性物件的一筆記錄，包括專案檔和專案專案檔案。  
  
## <a name="see-also"></a>另請參閱  
 [執行中的檔資料表](../../extensibility/internals/running-document-table.md)   
 [IDE 中的選取項目和貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)
