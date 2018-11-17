---
title: 實作單一檔案產生器 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 36aa6df6c0b904ad11f0027c4e01368a9c864b8a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781660"
---
# <a name="implementing-single-file-generators"></a>實作單一檔案產生器
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

自訂工具 — 有時稱為單一檔案產生器，可用來擴充[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]並[!INCLUDE[csprcs](../../includes/csprcs-md.md)]專案中的系統[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。 自訂工具是實作的 COM 元件<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>介面。 使用此介面，自訂工具將轉換成單一的輸出檔案的單一輸入的檔案。 轉換的結果可能是原始碼或任何其他輸出，是很有用。 自訂工具產生的程式碼檔案的兩個範例會產生以回應在視覺化設計工具和使用 Web 服務描述語言 (WSDL) 產生的檔案中變更程式碼。  
  
 當載入自訂的工具，或輸入的檔案儲存時，專案系統會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>方法，並將參考傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>回呼介面，藉此工具時，可以向使用者報告其進度。  
  
 自訂工具產生的輸出檔案會加入至專案的相依性的輸入檔。 專案系統會自動判斷輸出檔案，根據自訂工具的實作所傳回的字串名稱<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>。  
  
 自訂工具必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>介面。 （選擇性） 自訂的工具支援<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>介面，以從輸入檔以外的來源擷取資訊。 在任何情況下，您可以使用自訂的工具，您必須先註冊它與系統或[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]本機登錄。 如需有關如何註冊自訂工具的詳細資訊，請參閱[註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)。  
  
## <a name="see-also"></a>另請參閱  
 [判斷專案的預設命名空間](../../misc/determining-the-default-namespace-of-a-project.md)   
 [將類型公開至視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)

