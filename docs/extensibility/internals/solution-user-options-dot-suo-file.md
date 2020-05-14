---
title: 解決方案使用者選項 (.Suo) 檔案 |微軟文件
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9469663d3ac258e1c568778894d8584c68c13632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705310"
---
# <a name="solution-user-options-suo-file"></a>方案使用者選項檔 (.Suo)
解決方案用戶選項 (.suo) 檔包含每個使用者的解決方案選項。 不應將此檔簽入原始程式碼控制。

 解決方案用戶選項 (.suo) 檔案是以二進位格式儲存的結構化存儲或複合檔案。 將使用者資訊保存到流中,其中流的名稱是用於標識 .suo 檔中的資訊的密鑰。 解決方案用戶選項檔案用於儲存使用者首選項設置,並在 Visual Studio 保存解決方案時自動創建。

 當環境打開 .suo 檔時,它會枚舉所有當前載入的 VS 包。 如果 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>實現了 介面,則環境調用 VSPackage 上<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A>的方法,要求其從 .suo 檔載入其所有數據。

 VSPackage 有責任知道它可能寫入了 .suo 檔中的流。 對於它編寫的每個流,VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>通過 載入由密鑰(即流的名稱)標識的特定流回環境。 然後,環境調用 VSPackage 讀取傳遞流的名稱和指向`IStream`<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>方法的指標的特定流。

 此時,將發出另一個調用,`LoadUserOptions`以查看是否還有必須讀取的 .suo 檔的另一個部分。 此過程將一直持續到環境讀取和處理 .suo 檔中的所有資料流。

 保存或關閉解決方案時,環境使用指向方法的<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A><xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>指標調用方法。 `IStream`包含要保存的二進位資訊將傳遞給<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>方法,該方法然後將資訊寫入 .suo 檔,然後`SaveUserOptions`再次調用 該方法以查看是否有另一個資訊流要寫入 .suo 檔。

 這兩種方法`SaveUserOptions``WriteUserOptions`與呼叫,對於要儲存到 .suo 檔的每個資訊串流,將指標`IVsSolutionPersistence`傳遞到 。 它們被遞歸地調用,以允許將多個流寫入 .suo 檔。 這樣,使用者資訊將隨解決方案一起保留,並保證在下次打開解決方案時會在那裡。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [方案](../../extensibility/internals/solutions-overview.md)
