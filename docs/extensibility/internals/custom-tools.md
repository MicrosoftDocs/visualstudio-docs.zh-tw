---
title: 自訂工具 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e60f1d8cb8b25ed50b0b20c5ebb538286687ad72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708951"
---
# <a name="custom-tools"></a>自訂工具
*自訂工具*允許您將工具與專案中的項目相關聯,並在保存檔時運行該工具。 某些自定義工具(有時稱為*單檔產生器*)通常用於實現從資料生成代碼的轉換器,反之亦然。 例如,單檔產生器從 *.設定*和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] *.resx*檔案建立[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和原始碼。 生成的原始碼提供對 *.設定*和 *.resx*檔案中的數據的強類型存取。 和[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)][!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案類型支援自定義工具;[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]項目類型不。 您自己的項目類型也可以支援自定義工具。

 自定義工具是實現介面的`IVsSingleFileGenerator`註冊元件。

 自定義工具與`ProjectItem`介面物件相關聯,並且類似於設計器和編輯器。 自訂工具將表示為輸入的文件`ProjectItem`作為輸入,並寫入其檔名`DefaultExtension`由方法提供的新檔。

## <a name="in-this-section"></a>本節內容
- [實現單檔產生器](../../extensibility/internals/implementing-single-file-generators.md)

 描述如何使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>介面實現自定義工具。

- [註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)

 提供自定義工具的所有註冊表項的說明。

- [以視覺化設計器公開類型](../../extensibility/internals/exposing-types-to-visual-designers.md)

 說明專案系統如何支援可視化設計人員通過臨時可移植可執行 (PE) 檔案存取生成的類和類型。

- [保留項目項目的屬性](../../extensibility/persisting-the-property-of-a-project-item.md)

 展示如何在專案檔中保留專案項屬性(如源檔的作者)。

## <a name="reference"></a>參考
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>提供有關的詳細資訊,<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>該檔將單個輸入檔案轉換為單個輸出檔,該檔可以編譯或添加到專案中。

 <xref:EnvDTE.ProjectItem>解釋`ProjectItem`表示專案中的項的介面。

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>提供有關`DefaultExtension`方法的詳細資訊,該方法檢索提供給輸出檔名的檔名副檔名。

## <a name="related-sections"></a>相關章節
- [延伸項目](../../extensibility/extending-projects.md)

 描述如何使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案和解決方案組織程式碼檔案和資源檔，以及如何實作原始檔控制。
