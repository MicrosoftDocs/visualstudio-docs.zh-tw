---
title: 解決方案使用者選項 (。.Suo) 檔案 |Microsoft Docs
description: 深入瞭解解決方案使用者選項 ( .suo) 檔案，其中包含以二進位格式儲存的結構化儲存體檔案中的每個使用者方案選項。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a978986ed6ef32dbad3ad06eafcba11d7f4782ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962908"
---
# <a name="solution-user-options-suo-file"></a>方案使用者選項檔 (.Suo)
方案使用者選項 ( .suo) 檔案包含每個使用者的方案選項。 此檔案不應簽入原始程式碼控制。

 方案使用者選項 ( .suo) 檔案是儲存為二進位格式的結構化儲存體或複合檔案。 您可以將使用者資訊儲存到資料流程中，該資料流程的名稱是用來識別 .suo 檔案中資訊的索引鍵。 方案使用者選項檔是用來儲存使用者喜好設定，並在 Visual Studio 儲存方案時自動建立。

 當環境開啟 .suo 檔案時，它會列舉目前載入的所有 Vspackage。 如果 VSPackage 實作為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> 介面，則環境 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> 會呼叫 VSPackage 上的方法，要求它從 .suo 檔案載入其所有資料。

 VSPackage 需要知道它可能已寫入 .suo 檔案的資料流程。 針對它所撰寫的每個資料流程，VSPackage 會透過呼叫至環境 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 以載入由索引鍵識別的特定資料流程，也就是資料流程的名稱。 然後環境會回呼至 VSPackage，以讀取傳遞資料流程名稱的特定資料流程和 `IStream` 方法的指標 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 。

 屆時會進行另一次呼叫，以查看是否有需要 `LoadUserOptions` 讀取之 .suo 檔案的另一個區段。 此程式會繼續進行，直到該 .suo 檔案中的所有資料流程都已由環境讀取和處理為止。

 當您儲存或關閉方案時，環境會 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> 使用方法的指標來呼叫方法 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> 。 `IStream`包含要儲存之二進位資訊的會傳遞至 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> 方法，然後將資訊寫入 .suo 檔案，然後 `SaveUserOptions` 再次呼叫方法，以查看是否有其他資訊資料流程要寫入 .suo 檔案中。

 這兩個方法（ `SaveUserOptions` 和 `WriteUserOptions` ）會以遞迴方式呼叫每個要儲存至 .suo 檔案的資料流程，並將指標傳入 `IVsSolutionPersistence` 。 它們是以遞迴方式呼叫，以允許將多個資料流程寫入 .suo 檔案。 如此一來，使用者資訊會與方案一起保存，並保證在下一次開啟方案時，會有此資訊。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [方案](../../extensibility/internals/solutions-overview.md)
