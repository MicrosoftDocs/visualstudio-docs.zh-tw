---
title: 方案使用者選項 (。Suo) 檔案 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f529a3861ed6061b428818140ad90d6ca79991af
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600863"
---
# <a name="solution-user-options-suo-file"></a>方案使用者選項檔 (.Suo)
方案使用者選項 (.suo) 檔案包含每個使用者方案的選項。 此檔案應該不會簽入原始程式碼控制項中。

 方案使用者選項 (.suo) 檔案是結構化儲存體或複合式的以二進位格式儲存的檔案。 您要將用來識別.suo 檔案中的資訊的索引鍵的資料流的名稱儲存到資料流的使用者資訊。 方案使用者選項檔用來儲存使用者喜好設定，並會在 Visual Studio 會儲存方案時自動建立。

 當環境隨即開啟.suo 檔案時，它會列舉所有目前載入的 Vspackage。 如果實作 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>介面，則環境會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A>要求它的 VSPackage，載入它的所有資料從.suo 檔案上的方法。

 它是 VSPackage 的責任，知道什麼資料流寫入.suo 檔案。 針對它撰寫每個資料流，VSPackage 回呼環境<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>載入特定的資料流所識別的索引鍵，也就是資料流的名稱。 環境然後回撥來讀取資料流的名稱傳遞該特定資料流 vspackage 以及`IStream`指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>方法。

 此時，另一個呼叫`LoadUserOptions`以查看是否有要讀取的.suo 檔案的另一個區段。 此程序會繼續直到所有的.suo 檔案中的資料流已讀取及處理環境。

 當此解決方案不會儲存或關閉，環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A>方法的指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>方法。 `IStream`包含儲存的二進位資訊傳遞給<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>方法，然後將資訊寫入至.suo 檔案，並在呼叫`SaveUserOptions`方法一次以查看是否有另一個要寫入資訊到.suo 的檔案資料流檔案。

 這兩種方法，`SaveUserOptions`並`WriteUserOptions`，會針對每個資料流的資訊儲存到.suo 檔案中，傳入的指標呼叫以遞迴方式`IVsSolutionPersistence`。 呼叫以遞迴方式，以允許進行的.suo 檔案的多個資料流寫入。 如此一來，使用者資訊與方案一起保存，一定會有下一次開啟方案時。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [方案](../../extensibility/internals/solutions.md)