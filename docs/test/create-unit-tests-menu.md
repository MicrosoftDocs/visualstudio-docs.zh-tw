---
title: 建立單元測試方法虛設常式
description: 瞭解如何使用 [建立單元測試] 命令，此命令可讓您輕鬆地設定測試專案、測試類別和其中的測試方法存根。
ms.custom: SEO-VS-2020
ms.date: 04/24/2020
ms.topic: how-to
helpviewer_keywords:
- unit testing, create unit tests
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 684c6254aac8bd45926759e0b6ad96cfe3f6c8ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964416"
---
# <a name="create-unit-test-method-stubs-from-code"></a>從程式碼建立單元測試方法存根

**Create Unit Tests** 命令可建立單元測試方法 Stub。 此功能允許輕鬆設定測試專案、測試類別，以及其內的測試方法虛設常式。

::: moniker range="vs-2017"
> [!NOTE]
> [ **建立單元測試** ] 功能表命令僅適用于以 .NET Framework (為目標的 c # 程式碼，但不適用於 .net Core 或 .NET Standard) 。
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> [ **建立單元測試** ] 功能表命令僅適用于 c # 程式碼。
::: moniker-end

[建立單元測試] 功能表命令可延伸，並可用來產生 MSTest、MSTest V2、NUnit 和 xUnit 測試。

## <a name="get-started"></a>開始使用

若要開始，請以滑鼠右鍵按一下您想要測試之專案程式碼編輯器中的方法、類型或命名空間，然後選擇 [建立單元測試]。 [建立單元測試] 對話方塊隨即開啟，您可以在此設定想要建立的測試方式。

![使用建立單元測試命令](media/createunittestcommand.png)

如果您沒有看到適用于 NUnit 或 xUnit 的測試架構選項，請參閱 [使用協力廠商單元測試](#use-third-party-unit-test-frameworks)架構。

## <a name="set-unit-test-traits"></a>設定單元測試特性

如果您計劃執行這些測試作為測試自動化程序的一部分，則可能會考慮在另一個測試專案中建立測試 (上述對話方塊中的第二個選項)，以及設定單元測試的單元測試特性。 這可讓您更輕鬆地包含或排除這些特定測試作為持續整合或持續部署管線的一部分。 特性是透過直接將中繼資料新增至單元測試所設定，如下所示。

![設定單元測試特性](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>使用協力廠商單元測試架構

若要自動產生 NUnit 或 xUnit 的單元測試，請從 Visual Studio Marketplace 安裝下列其中一個測試架構延伸模組：

* [測試產生器的 NUnit 延伸模組](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [測試產生器的 xUnit.net 延伸模組](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>何時應該使用這項功能？

每當您需要建立單元測試，特別是當您要測試僅有少量或沒有測試涵蓋範圍，且沒有文件的現有程式碼時，請使用此功能。 換句話說，其中具有有限或不存在的程式碼規格。 它會有效地實作與[類似的方法](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/)，描述觀察到的程式碼行為特性。

不過，這項功能也同樣適用於開發人員開始撰寫一些程式碼，並用它啟動單元測試的情況。 在編碼流程內，開發人員可能想要快速建立特定程式碼片段的單元測試方法 Stub (具有適當的測試類別和測試專案)。

## <a name="see-also"></a>另請參閱

- [使用 [建立單元測試] 來建立單元測試方法虛設常式](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/) \(英文\)
- [單元測試部落格文章](https://devblogs.microsoft.com/devops/?s=unit+testing) \(英文\)
