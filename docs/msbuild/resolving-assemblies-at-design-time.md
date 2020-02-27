---
title: 在設計階段時解析組件 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69f5ba2627e2d659665fa0bd3fbf706f9cad5573
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632559"
---
# <a name="resolve-assemblies-at-design-time"></a>在設計階段解析組件

當您透過 [加入參考] 對話方塊的 [.NET] 索引標籤加入組件的參考時，參考會指向中繼參考組件，也就是說，這個組件會包含所有類型和簽章資訊，但不一定會包含任何程式碼。 [.NET] 索引標籤會列出對應至 .NET Framework 中執行階段組件的參考組件。 此外，它列出的參考組件會對應至協力廠商使用的已註冊 AssemblyFoldersEx 資料夾中的執行階段組件。

## <a name="multi-targeting"></a>多目標

 Visual Studio 可讓您以在多個版本的 .NET Framework 上執行的 .NET Framework 版本為目標。 發行新的 .NET Framework 版本時，可以使用目標套件來安裝架構，而且它會自動顯示為 Visual Studio 中的目標。

## <a name="how-type-resolution-works"></a>類型解析如何運作

 在執行時間，CLR 會藉由查看 GAC、 *bin*目錄及任何探查路徑來解析元件中的類型。 這是由融合載入器處理。 但融合載入器如何知道所要尋找的目標呢？ 這會根據在設計階段建置應用程式時的解析結果而定。

 在建置期間，編譯器會使用參考組件來解析應用程式類型。 在 .NET Framework 2.0、3.0、3.5、4、4.5 和 4.5.1 版中，參考組件會在安裝 .NET Framework 時一起安裝。

 參考組件是由目標套件提供，該目標套件隨附於對應的 .NET Framework SDK 版本中。 Framework 本身只會提供執行階段組件。 您必須安裝 .NET Framework 和對應的.NET Framework SDK，才能建置應用程式。

 當您以特定的 .NET Framework 為目標時，建置系統會使用目標套件中的參考組件來解析所有類型。 在執行時間，融合載入器會將這些相同的類型解析為執行時間元件，通常位於 GAC 中。

 如果無法使用參考組件時，建置系統會使用執行階段組件來解析組件類型。 因為無法根據次要版本號碼來區分 GAC 中的執行階段組件，所以可能會解析為錯誤的組件。 例如，當 .NET Framework 3.5 版中引入的新方法以 3.0 版為目標時，就會發生這種情形。 建置將會成功，而且應用程式可在組建電腦上執行，但部署至沒有安裝 3.5 版的電腦時則會失敗。

 現在隨附於 .NET Framework SDK 的目標套件包含 Framework 版本中所有執行階段組件的清單，稱為轉散發 (redist) 清單，使組建系統無法針對錯誤的組件版本解析類型。

## <a name="see-also"></a>另請參閱
- [進階概念](../msbuild/msbuild-advanced-concepts.md)
