---
title: 實作單一檔案產生器 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71db8036634cfc266db3c585c48317262f48b367
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-single-file-generators"></a>實作單一檔案產生器
自訂工具，有時也稱為單一檔案產生器，可用於延伸[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案中的系統[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 自訂工具是 COM 元件，可實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>介面。 使用此介面，自訂的工具將轉換成單一輸出檔案的單一輸入的檔案。 轉換的結果可能會是原始碼或任何其他輸出很有用。 自訂工具產生的程式碼檔案的兩個範例會產生回應的視覺化設計工具和使用 Web 服務描述語言 (WSDL) 產生的檔案中變更程式碼。  
  
 當載入自訂工具時，或輸入的檔案儲存時，專案系統會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>方法，並將參考傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>回呼介面，藉此工具可以向使用者報告其進度。  
  
 自訂工具產生的輸出檔會加入至專案的相依性輸入檔。 專案系統會自動決定的輸出檔為基礎的自訂工具的實作所傳回的字串名稱<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>。  
  
 自訂工具必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>介面。 （選擇性） 使用的自訂工具支援<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>介面，以從輸入檔以外的來源中擷取資訊。 在任何情況下，您可以使用自訂工具之前，您必須註冊此系統，或在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本機登錄。 如需註冊的自訂工具的詳細資訊，請參閱[註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將類型公開至視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)