---
title: 將 Web 服務加入專案系統 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: 80de75b1b10a761e88b86c0982c0dc925c6eeeb4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47489088"
---
# <a name="adding-web-services-to-project-systems"></a>將 Web 服務加入專案系統中
XML Web service 在一般情況下，是以程式設計方式的資訊傳回給專案系統使用的 SOAP (Simple Object Access Protocol) 通訊協定的 URL 定址資源。 您也可以使用 VSPackage 專案系統整合的 Web 服務<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2>介面。  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>若要將 Web 服務新增至您的專案系統  
  
1.  呼叫`QueryService`for<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2>介面透過<xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg>服務。  
  
2.  呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> 方法。 如果您傳入`pDiscoverySession`做為參數`NULL`、 為您建立探索工作階段和工作階段會快取，使其可供後續使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>介面。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> 方法會傳回的指標<xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>。  
  
3.  呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> 方法。 為 Web 服務參考 資料夾中的 automation 物件傳遞`pUnkWebReferenceFolder`參數。 Visual Studio 環境然後會檢查是否已經有 Web 服務。 如果 Web 服務不存在，則環境下載，並將 Web 服務加入至資料夾和任何其他檔案 （例如.wsdl 檔案） 的資料夾之子節點。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>