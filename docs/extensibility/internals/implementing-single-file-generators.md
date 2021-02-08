---
title: 執行 Single-File 產生器 |Microsoft Docs
description: '瞭解如何使用自訂工具來執行 IVsSingleFileGenerator 介面，以擴充 Visual Studio 中的 Visual Basic 和 Visual c # 專案系統。'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e353101c7932e06042b451360b7ca040adcb303f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839946"
---
# <a name="implementing-single-file-generators"></a>實作單一檔案產生器
自訂工具（有時稱為單一檔案產生器）可用來擴充 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 和 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 中的專案系統 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 自訂工具是可實介面的 COM 元件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 。 使用這個介面時，自訂工具會將單一輸入檔轉換成單一輸出檔。 轉換的結果可能是原始程式碼，或任何其他有用的輸出。 自訂工具產生的程式碼檔案有兩個範例，是為了回應視覺化設計工具中的變更而產生的程式碼，以及使用 Web 服務描述語言 (WSDL) 產生的檔案。

 載入自訂工具或儲存輸入檔時，專案系統會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> 方法，並傳遞 <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> 回呼介面的參考，讓此工具可以向使用者報告其進度。

 自訂工具產生的輸出檔會加入至具有輸入檔相依性的專案。 專案系統會根據自訂工具的執行所傳回的字串，自動決定輸出檔的名稱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> 。

 自訂工具必須執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> 介面。 （選擇性）自訂工具支援 <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> 介面，以從輸入檔以外的來源取得資訊。 在任何情況下，您必須先向系統或在本機登錄中註冊，才能使用自訂工具 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 如需註冊自訂工具的詳細資訊，請參閱 [註冊單一](../../extensibility/internals/registering-single-file-generators.md)檔案產生器。

## <a name="see-also"></a>另請參閱
- [將類型公開至視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)
