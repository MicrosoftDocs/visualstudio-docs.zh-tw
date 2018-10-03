---
title: 專案優先順序 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 57698e78c9228177e7f078cd725c1d4571e36d76
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499061"
---
# <a name="project-priority"></a>專案優先順序
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

本主題的最新的版本可從[專案優先順序](https://docs.microsoft.com/visualstudio/extensibility/internals/project-priority)。  
  
專案項目通常是在方案中只能有一個專案的成員。 因此，IDE 可以輕易地判斷哪一個專案用來開啟項目中。 不過，如果項目是多個專案的成員，IDE 會判斷最佳的專案開啟的項目使用的優先順序配置。  
  
 下列清單顯示專案的優先順序配置：  
  
-   IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A>解決方案可以判斷文件是否屬於該專案中每個專案的方法。  
  
-   如果文件是專案的成員，專案會回應以優先順序專案會指派它處理該文件的根據。 比方說，語言專案以高優先順序，其語言原始程式檔，但具有較低的優先順序，不會在其組建程序無法辨識的檔案類型的回應。  
  
-   提供自訂的專案特定的編輯器或設計工具文件的專案也會收到高的優先順序。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列舉型別提供的文件的優先順序值。  
  
-   指定的最高優先權的專案有開啟的文件的內容。 如果兩個專案傳回相等的優先順序值，使用中的專案是慣用的。 如果方案中的沒有專案回應，它可以開啟文件，則 IDE 會將文件置於其他檔案專案。 如需詳細資訊，請參閱 <<c0> [ 其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)。  
  
## <a name="see-also"></a>另請參閱  
 [其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)   
 [如何： 開啟編輯器開啟的文件](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)

