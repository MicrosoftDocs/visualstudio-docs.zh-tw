---
title: "原始檔控制的設計決策 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 320a8013177d44491470f8f55c8ee3e1fb19501c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-design-decisions"></a>原始檔控制的設計決策
實作原始檔控制時，應該考量下列設計決策的專案。  
  
## <a name="will-information-be-shared-or-private"></a>資訊將會共用或私用嗎？  
 您可以讓最重要的設計決策是何種資訊可共用以及什麼是私人。 比方說，共用之專案檔案的清單，但在此清單檔案中，某些使用者可能會想要的私人檔案。 會共用編譯器設定，但通常私用的啟始專案。 設定是單純地共用、 共用使用覆寫，或單純私用。 根據設計，私用的項目，例如方案使用者選項 (.suo) 檔案未簽入[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]。 請務必將任何私人資訊儲存在私用的檔案，例如.suo 檔案中或您建立時，例如，特定私人檔案。 Visual C# 的檔案副檔名為.csproj.user 或。 Visual Basic 的.vbproj.user 檔案。  
  
 這個決定不是全部包含，才能進行項目為基礎。  
  
## <a name="will-the-project-include-special-files"></a>專案會包含特殊的檔案嗎？  
 另一個重要的設計決策就是您的專案結構是否會使用特殊的檔案。 特殊的檔案是隱藏的檔案為基礎的檔案會顯示在方案總管和簽入和簽出對話方塊。 如果您使用特殊的檔案，請遵循這些指導方針：  
  
1.  請勿將特殊的檔案關聯之專案的根節點，也就是與專案檔案本身。 您的專案檔必須是單一檔案。  
  
2.  當新增、 移除或重新命名專案中，適當的特殊檔案<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>設定旗標，指出檔案是特殊的檔案，必須引發事件。 專案中呼叫適當的回應中的環境會呼叫這些事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>方法。  
  
3.  當您的專案或編輯器呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>檔案，該檔案相關聯的特殊檔案不會自動簽出。傳遞中的特殊檔案，以及父檔案。 環境會偵測會在傳遞的所有檔案之間的關聯性，並適當地隱藏簽出 UI 中的特殊檔案。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)