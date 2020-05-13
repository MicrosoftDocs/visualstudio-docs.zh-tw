---
title: 實現單檔產生器 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e700d09277edbb04b30676d3965b6c996d0a11f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707662"
---
# <a name="implementing-single-file-generators"></a>實作單一檔案產生器
自訂工具(有時稱為單個檔產生器)可用於擴展和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)][!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案系統。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 自訂工具是實現介面的<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>COM 元件。 使用此介面,自定義工具將單個輸入檔案轉換為單個輸出檔。 轉換的結果可能是原始碼或任何其他有用的輸出。 自訂工具生成的代碼檔的兩個範例是回應可視化設計器中的更改和使用 Web 服務描述語言 (WSDL) 生成的檔案生成的代碼。

 載入自訂工具或保存輸入檔時,專案系統將調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>該方法,並將引用傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>給回調介面,以便該工具可以向使用者報告其進度。

 自訂工具生成的輸出檔將添加到依賴於輸入檔的專案中。 專案系統根據自訂工具的完整的字串自動決定輸出檔的名稱<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>。

 自定義工具必須實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>介面。 或者,自定義工具支援<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>介面從輸入檔以外的源檢索資訊。 在任何情況下,在可以使用自定義工具之前,必須將其註冊到系統或[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本地註冊表中。 有關註冊自訂工具的詳細資訊,請參閱[註冊單個檔產生器](../../extensibility/internals/registering-single-file-generators.md)。

## <a name="see-also"></a>另請參閱
- [將類型公開至視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)
