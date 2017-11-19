---
title: "持續性和執行文件資料表 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 062c623ec1de779733e41a8abcad8ca478155dba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="persistence-and-the-running-document-table"></a>持續性和執行 Document 資料表
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE，專案會完全負責管理其專案，這些項目他們完成使用服務時，持續性<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>。 文件是在 Visual Studio 環境中的持續性的基本單位。 專案協調開啟、 儲存及重新命名的文件與執行文件資料表 (RDT)，會追蹤所有開啟的文件的狀態的資源。  
  
## <a name="managing-persistence"></a>管理持續性  
 專案控制藉由實作環境的持續性服務<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>介面。 當環境永遠不會直接要求保存本身的文件時，它會要求儲存文件的主控專案 （或階層）。 這可讓專案以將其專案項目資料儲存至本機檔案、 遠端檔案、 資料庫、 儲存機制或其他媒體。  
  
 全域環境維護 RDT。 環境會維護所有開啟的視窗項目和 RDT，這樣就能讓他們的文件接收到特殊的通知，例如當關閉方案。 此外，RDT 使得要追蹤其對應的節點中的環境**方案總管 中**。 RDT 會維護每個開啟的、 永續性的物件，包括專案檔和專案項目文件的一筆記錄。  
  
## <a name="see-also"></a>另請參閱  
 [執行中的文件表格](../../extensibility/internals/running-document-table.md)   
 [IDE 中的選取項目和貨幣](../../extensibility/internals/selection-and-currency-in-the-ide.md)