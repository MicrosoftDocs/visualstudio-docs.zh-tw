---
title: 解決方案概觀
description: 瞭解解決方案的內部，適用于想要使用 Visual Studio 擴充功能中解決方案的延伸模組開發人員。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 91903954f490e5845e01ddbf4b7aa4767f2ceacc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99846539"
---
# <a name="solutions-overview"></a>解決方案概觀

方案是一或多個專案的群組，這些專案會一起運作來建立應用程式。 與解決方案有關的專案和狀態資訊會儲存在兩個不同的方案檔中。 [方案 ( .sln) ](solution-dot-sln-file.md)檔案是以文字為基礎，而且可以放在原始程式碼控制之下，並且在使用者之間共用。 [方案使用者選項 ( .suo) ](solution-user-options-dot-suo-file.md)檔案是二進位檔案。 因此，.suo 檔案不能放在原始程式碼控制之下，並且包含使用者特定的資訊。

任何 VSPackage 都可以寫入至任一種類型的方案檔。 由於檔案的本質，因此有兩個不同的介面可以寫入它們。 介面會將 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> 文字資訊寫入 .sln 檔案，而介面會將 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> 二進位資料流程寫入 .suo 檔案中。

> [!NOTE]
> 專案不需要明確地將專案寫入至方案檔;環境會處理專案的。 因此，除非您想要特別將其他內容新增至方案檔，否則您不需要以這種方式註冊您的 VSPackage。

支援解決方案持續性的每個 VSPackage 都會使用三個介面，也 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 就是由環境所執行並由 VSPackage 呼叫的介面，以及由 `IVsPersistSolutionProps` VSPackage 所 `IVsPersistSolutionOpts` 執行的和。 `IVsPersistSolutionOpts`只有在 VSPackage 將私用資訊寫入 .suo 檔案時，才需要實作為介面。

開啟方案時，會進行下列處理。

1. 環境會讀取方案。

2. 如果環境找到 `CLSID` ，就會載入對應的 VSPackage。

3. 如果載入 VSPackage，環境會針對 `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> VSPackage 需要的介面呼叫介面。

   - 從 .sln 檔案讀取時，環境會呼叫 `QueryInterface` `IVsPersistSolutionProps` 。

   - 從 .suo 檔案讀取時，環境會呼叫 `QueryInterface` `IVsPersistSolutionOpts` 。

   您可以在 [方案 (] 中找到這些檔案的使用相關特定資訊 [。.Sln) ](../../extensibility/internals/solution-dot-sln-file.md) 檔案和 [方案使用者選項 (。.Suo) ](../../extensibility/internals/solution-user-options-dot-suo-file.md)檔案。

> [!NOTE]
> 如果您想要建立包含兩個專案設定的新解決方案設定，並從組建中排除第三個專案，您必須使用屬性頁 UI 或自動化。 您無法直接變更方案組建管理員設定和其屬性，但是您可以使用 `SolutionBuild` 自動化模型中 DTE 的類別來操作方案組建管理員。 如需設定解決方案的詳細資訊，請參閱 [方案](../../extensibility/internals/solution-configuration.md)設定。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
