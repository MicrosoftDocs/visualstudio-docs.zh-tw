---
title: 建立單元測試方法虛設常式
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- unit testing, create unit tests
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 577cb338e7cbf20b23d2d75ad2dfded017b0aacb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955137"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>使用建立單元測試命令來建立單元測試方法虛設常式

Visual Studio [建立單元測試] 命令可讓您建立單元測試方法虛設常式。 此功能允許輕鬆設定測試專案、測試類別，以及其內的測試方法虛設常式。

## <a name="availability-and-extensions"></a>可用性和延伸模組

[建立單元測試] 功能表命令：

* 適用於 Visual Studio 2015 和更新版本的 Community、Professional 和 Enterprise Edition。

* 只支援以 .NET Framework 為目標的 C# 程式碼。

* 可擴充，並且支援以 MSTest、MSTest V2、NUnit、xUnit 格式發出測試。

* 尚無法於 .NET Core 專案中使用。

## <a name="get-started"></a>開始使用

若要開始，請在您想要測試之專案的程式碼編輯器中選取方法、類型或命名空間，並開啟捷徑功能表，然後選擇 [建立單元測試]。 [建立單元測試] 對話方塊隨即開啟；在其中，可以選取新單元測試的建立選項。

![使用建立單元測試命令](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>設定單元測試特性

如果您計劃執行這些測試作為測試自動化程序的一部分，則可能會考慮在另一個測試專案中建立測試 (上述對話方塊中的第二個選項)，以及設定單元測試的單元測試特性。 這可讓您更輕鬆地包含或排除這些特定測試作為持續整合或持續部署管線的一部分。 特性是透過直接將中繼資料新增至單元測試所設定，如下所示。

![設定單元測試特性](media/createunittest.png)

## <a name="using-third-party-unit-test-frameworks"></a>使用協力廠商單元測試架構

使用 Visual Studio，您可以使用任何測試架構輕鬆地建立單元測試。 若要安裝其他測試架構：

1. 選擇 [工具] > [延伸模組和更新]。
2. 依序展開 [線上] > [Visual Studio Marketplace] > [工具]，然後選擇 [測試]。

![使用協力廠商測試架構](media/createunittestfx.png)

Visual Studio Marketplace 提供測試架構延伸模組︰

* [測試產生器的 NUnit 延伸模組](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [測試產生器的 xUnit.net 延伸模組](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>何時應該使用這項功能？

只要您需要建立單元測試，但特別是當您要測試僅有少量或沒有測試涵蓋範圍且沒有文件的現有程式碼時，就會使用此功能。 換句話說，其中具有有限或不存在的程式碼規格。 它會有效地實作與 [Smart unit tests](https://blogs.msdn.microsoft.com/devops/2014/11/19/introducing-smart-unit-tests/) (智慧型單元測試) 類似的方法，以描述觀察到的程式碼行為。

不過，這項功能也同樣適用於這種情況；其中，開發人員會開始撰寫某個程式碼，並使用該程式碼來啟動單元測試專業領域。 在編碼流程內，開發人員可能想要快速建立特定程式碼部分的單元測試方法虛設常式 (具有適當的測試類別，以及適當的測試專案)。

## <a name="see-also"></a>另請參閱

- [使用 [建立單元測試] 來建立單元測試方法虛設常式](https://blogs.msdn.microsoft.com/devops/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/) \(英文\)
- [單元測試部落格文章](https://blogs.msdn.microsoft.com/devops/?s=unit+testing) \(英文\)
