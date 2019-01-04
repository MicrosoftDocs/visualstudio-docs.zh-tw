---
title: 實作單一檔案產生器 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 728a1748d4c78bd93bf827290404f65607076b6a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53847778"
---
# <a name="implementing-single-file-generators"></a>實作單一檔案產生器
自訂工具 — 有時稱為單一檔案產生器，可用來擴充[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]並[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案中的系統[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 自訂工具是實作的 COM 元件<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>介面。 使用此介面，自訂工具將轉換成單一的輸出檔案的單一輸入的檔案。 轉換的結果可能是原始碼或任何其他輸出，是很有用。 自訂工具產生的程式碼檔案的兩個範例會產生以回應在視覺化設計工具和使用 Web 服務描述語言 (WSDL) 產生的檔案中變更程式碼。  
  
 當載入自訂的工具，或輸入的檔案儲存時，專案系統會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>方法，並將參考傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>回呼介面，藉此工具時，可以向使用者報告其進度。  
  
 自訂工具產生的輸出檔案會加入至專案的相依性的輸入檔。 專案系統會自動判斷輸出檔案，根據自訂工具的實作所傳回的字串名稱<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>。  
  
 自訂工具必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>介面。 （選擇性） 自訂的工具支援<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>介面，以從輸入檔以外的來源擷取資訊。 在任何情況下，您可以使用自訂的工具，您必須先註冊它與系統或[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本機登錄。 如需有關如何註冊自訂工具的詳細資訊，請參閱[註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)。  
  
## <a name="see-also"></a>另請參閱  
 [將類型公開至視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)