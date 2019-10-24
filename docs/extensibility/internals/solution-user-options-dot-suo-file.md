---
title: 方案使用者選項（.Suo）檔案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f21e4a4a6530692709247e64b0d84aa7b06eb3a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723805"
---
# <a name="solution-user-options-suo-file"></a>方案使用者選項檔 (.Suo)
方案使用者選項檔（.suo）包含每個使用者的方案選項。 這個檔案不應簽入原始程式碼控制中。

 方案使用者選項（.suo）檔案是以二進位格式儲存的結構化儲存區或複合檔案案。 將使用者資訊儲存在資料流程中，並將資料流程的名稱指定為要用來識別 .suo 檔案中資訊的索引鍵。 方案使用者選項檔案是用來儲存使用者喜好設定，而且會在 Visual Studio 儲存方案時自動建立。

 當環境開啟 .suo 檔案時，它會列舉所有目前載入的 Vspackage。 如果 VSPackage 會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> 介面，則環境會呼叫 VSPackage 上的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> 方法，要求它從 .suo 檔案載入其所有資料。

 VSPackage 必須負責知道它可能已寫入 .suo 檔案的資料流程。 VSPackage 會針對它所撰寫的每個資料流程，透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 來回呼環境，以載入由索引鍵所識別的特定資料流程，也就是資料流程的名稱。 環境接著會回呼至 VSPackage，以讀取將資料流程名稱和 `IStream` 指標傳遞至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 方法的特定資料流程。

 此時，會對 `LoadUserOptions` 進行另一個呼叫，以查看是否有其他必須讀取的 .suo 檔案區段。 此程式會繼續進行，直到所有 .suo 檔案中的資料流程都已由環境讀取及處理為止。

 儲存或關閉方案時，環境會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> 方法的指標來呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> 方法。 包含要儲存之二進位資訊的 `IStream` 會傳遞至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> 方法，然後將資訊寫入 .suo 檔案，然後再次呼叫 `SaveUserOptions` 方法，以查看是否有另一個要寫入 .suo 檔案的資訊資料流程。

 這兩種方法（`SaveUserOptions` 和 `WriteUserOptions`）會以遞迴方式針對要儲存至 .suo 檔案的每個資訊資料流程呼叫，並將指標傳入 `IVsSolutionPersistence`。 它們會以遞迴方式呼叫，以允許寫入 .suo 檔案的多個資料流程。 如此一來，就會在解決方案中保存使用者資訊，並保證在下一次開啟方案時可以使用。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [方案](../../extensibility/internals/solutions-overview.md)