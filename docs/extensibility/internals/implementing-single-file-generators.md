---
title: 執行單一檔案產生器 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69bde665e62d063b6bab8784634777eeea02e941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727169"
---
# <a name="implementing-single-file-generators"></a>實作單一檔案產生器
自訂工具（有時也稱為單一檔案產生器）可以用來擴充 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中的 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 和 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案系統。 自訂工具是可執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 介面的 COM 元件。 使用此介面時，自訂工具會將單一輸入檔案轉換成單一輸出檔案。 轉換的結果可能是原始程式碼，或任何其他有用的輸出。 自訂工具產生的程式碼檔案有兩個範例，就是為了回應視覺化設計工具中的變更，以及使用 Web 服務描述語言（WSDL）所產生的檔案而產生的程式碼。

 載入自訂工具或儲存輸入檔時，專案系統會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 方法，並將參考傳遞給 <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> 回呼介面，讓工具可以向使用者報告其進度。

 自訂工具產生的輸出檔會加入至具有輸入檔案相依性的專案。 專案系統會根據自訂工具的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>執行所傳回的字串，自動決定輸出檔的名稱。

 自訂工具必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 介面。 （選擇性）自訂工具支援 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> 介面，以從輸入檔以外的來源抓取資訊。 在任何情況下，您都必須先向系統或 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 本機登錄中註冊，才能使用自訂工具。 如需註冊自訂工具的詳細資訊，請參閱[註冊單一](../../extensibility/internals/registering-single-file-generators.md)檔案產生器。

## <a name="see-also"></a>請參閱
- [將類型公開至視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)