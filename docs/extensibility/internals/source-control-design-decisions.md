---
title: 原始檔控制的設計決策 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f47e0bdcf5b8dd3a7c41004ce82fca9f92db509e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936823"
---
# <a name="source-control-design-decisions"></a>原始檔控制的設計決策
實作原始檔控制時，下列設計決策應該視為專案。  
  
## <a name="will-information-be-shared-or-private"></a>資訊將會是共用或私用嗎？  
 最重要的設計決策，您可以進行是何種資訊是可共用私用。 比方說，共用的專案檔案的清單，但在此清單的檔案中，某些使用者可能會想要的私人檔案。 編譯器設定為共用，但是是一般私用的啟始專案。 設定是純粹共用，共用使用覆寫，或單純私用。 根據設計，私用的項目，例如方案使用者選項 (.suo) 檔案未簽入[!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]。 請務必將任何私人資訊儲存在私用的檔案，例如.suo 檔案中或您建立時，例如，特定私人檔案.csproj.user Visual C# 的檔案或.vbproj.user Visual basic 中的檔案。  
  
 這項決定不是全部包含，並可將項目由項目為基礎。  
  
## <a name="will-the-project-include-special-files"></a>專案包含特殊的檔案？  
 另一個重要的設計決策是您的專案結構是否使用特殊的檔案。 特殊的檔案是隱藏的檔案為基礎所顯示在 [方案總管] 中，並在簽入和簽出對話方塊的檔案。 如果您使用特殊的檔案，請遵循這些指導方針：  
  
1.  請勿將特殊的檔案關聯的專案根節點 — 也就是與專案檔案本身。 您的專案檔必須是單一檔案。  
  
2.  當新增、 移除或重新命名專案中，適當的特殊檔案<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>設定旗標，指出檔案是特殊的檔案，必須引發事件。 回應呼叫適當的專案中的環境會呼叫這些事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>方法。  
  
3.  當您的專案或編輯器呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>檔案，該檔案相關聯的特殊檔案不會自動簽出。中的特殊檔案與一起傳遞的父檔案。 環境會偵測傳入的所有檔案之間的關聯性，並適當地隱藏在 UI 中簽出的特殊檔案。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)