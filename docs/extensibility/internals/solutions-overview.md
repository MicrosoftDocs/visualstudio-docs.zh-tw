---
title: 解決方案概觀
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767db749d953855cd5c6f81f356a195c830aa838
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705303"
---
# <a name="solutions-overview"></a>解決方案概觀

解決方案是一個或多個專案分組,這些專案協同工作以創建應用程式。 與解決方案相關的項目和狀態資訊存儲在兩個不同的解決方案檔中。 [解決方案 (.sln) 檔案](solution-dot-sln-file.md)基於文字,可以置於原始程式碼控制之下並在用戶之間共用。 [解決方案用戶選項 (.suo) 檔案](solution-user-options-dot-suo-file.md)是二進位的。 因此,.suo 檔不能置於原始程式碼控制之下,並且包含特定於使用者的資訊。

任何 VSPackage 都可以寫入任一類型的解決方案檔。 由於文件的性質,實現兩個不同的介面來寫入它們。 介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>將文字資訊寫入 .sln<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>檔, 並且介面將二進位流寫入 .suo 檔。

> [!NOTE]
> 專案不必將自己的條目顯式寫入解決方案檔中;因此,專案不必將自己的條目顯式寫入解決方案檔中。環境處理專案的。 因此,除非要專門向解決方案檔添加其他內容,否則無需以這種方式註冊 VSPackage。

每個支援解決方案持久性的 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>使用三 個介面:由環境實現並由 VSPackage`IVsPersistSolutionProps`調`IVsPersistSolutionOpts`用的介面和和,它們都由 VSPackage 實現。 僅當`IVsPersistSolutionOpts`VSPackage 要將私有資訊寫入 .suo 檔時,才需要實現該介面。

打開解決方案時,將發生以下過程。

1. 環境讀取解決方案。

2. 如果環境找到`CLSID`, 它將載入相應的 VSPackage。

3. 如果載入了 VSPackage,環境將`QueryInterface`<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>請求 VSPackage 所需的介面的介面。

   - 從 .sln 檔案讀取時,`QueryInterface``IVsPersistSolutionProps`環境需要 。

   - 從 .suo 檔案讀取時,`QueryInterface``IVsPersistSolutionOpts`環境需要 。

   有關這些檔使用的具體資訊,請參閱[解決方案 (。Sln)](../../extensibility/internals/solution-dot-sln-file.md)檔案和[解決方案使用者選項 (。Suo) 檔案](../../extensibility/internals/solution-user-options-dot-suo-file.md)。

> [!NOTE]
> 如果要創建新的解決方案配置,包括兩個專案的配置,並且從生成中排除三分之一,則需要使用屬性頁 UI 或自動化。 不能直接更改解決方案生成管理器配置及其屬性,但可以使用自動化模型中 DTE`SolutionBuild`中的 類操作解決方案生成管理器。 有關設定解決方案的詳細資訊,請參閱[解決方案設定](../../extensibility/internals/solution-configuration.md)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
