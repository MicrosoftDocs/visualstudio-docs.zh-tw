---
title: 將 Web 服務加入至專案系統 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: f5b192be8e5f68ad9314fe08fff963c032013cb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002661"
---
# <a name="adding-web-services-to-project-systems"></a>將 Web 服務加入專案系統中
XML Web Service 通常是 URL 可定址的資源，會使用 SOAP (簡易物件存取通訊協定) 通訊協定，將程式設計資訊傳回專案系統。 您可以使用介面將 Web 服務整合到您的 VSPackage 專案系統 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> 。  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>將 Web 服務加入至您的專案系統  
  
1. `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> 透過服務呼叫介面 <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> 。  
  
2. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> 方法。 如果您將 `pDiscoverySession` 參數傳入 `NULL` ，系統就會為您建立探索會話，並快取會話，讓介面可供後續使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> 。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> 方法會傳回的指標 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2> 。  
  
3. 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> 方法。 傳入 Web 服務 [參考] 資料夾的 automation 物件做為 `pUnkWebReferenceFolder` 參數。 然後 Visual Studio 環境會檢查 Web 服務是否已存在。 如果 Web 服務不存在，則環境會下載 Web 服務，並將其加入至資料夾，以及任何其他檔案 (例如，) 到資料夾的子節點。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>