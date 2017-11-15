---
title: "使用建立單元測試命令來建立單元測試方法虛設常式 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: unit testing, create unit tests
ms.assetid: 5D625021-BA96-48A5-9453-3EF6F0943466
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: 7e69218700314224f67094486cfd381ac1460995
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>使用建立單元測試命令來建立單元測試方法虛設常式

Visual Studio [建立單元測試] 命令可讓您建立單元測試方法虛設常式。 此功能允許輕鬆設定測試專案、測試類別，以及其內的測試方法虛設常式。 

## <a name="availability-and-extensions"></a>可用性和延伸模組

[建立單元測試] 功能表命令：

* 適用於 Visual Studio 2015 和更新版本的 Community、Professional 和 Enterprise Edition。

* 只支援以 .NET Framework 為目標的 C# 程式碼。

* [可擴充](#extend-framework)，並且支援以 MSTest、MSTest V2、NUnit、xUnit 格式發出測試。

## <a name="get-started"></a>開始使用

若要開始，請在您想要測試之專案的程式碼編輯器中選取方法、類型或命名空間，並開啟捷徑功能表，然後選擇 [建立單元測試]。 這會開啟 [建立單元測試] 對話方塊，在其中，可以選取新單元測試的建立選項。

![使用建立單元測試命令](media/createunittestcommand.png)

## <a name="setting-unit-test-traits"></a>設定單元測試特性

如果您計劃執行這些測試是測試自動化程序的一部分，則可能會考慮在另一個測試專案中建立測試 (上述對話方塊中的第二個選項)，以及設定單元測試的單元測試特性。 這可讓您更輕鬆地包含或排除這些特定測試作為持續整合或持續部署管線的一部分。 特性是透過直接將中繼資料新增至單元測試所設定，如下所示。 

![設定單元測試特性](media/createunittest.png)

<a name="extend-framework"></a>
## <a name="using-third-party-unit-test-frameworks"></a>使用協力廠商單元測試架構

使用 Visual Studio，您可以使用任何測試架構輕鬆地建立單元測試。 若要安裝和新增其他測試架構，請選擇 [工具] | [延伸模組和更新]。
依序展開 [線上]、[Visual Studio 組件庫] 和 [工具]，然後選擇 [測試]。 

![使用協力廠商測試架構](media/createunittestfx.png)

Visual Studio Marketplace 提供測試架構延伸模組︰

* [測試產生器的 NUnit 延伸模組](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)
* [測試產生器的 xUnit.net 延伸模組](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)

## <a name="when-should-i-use-this-feature"></a>何時應該使用這項功能？

只要您需要建立單元測試，但特別是當您要測試有很少或沒有測試涵蓋範圍且沒有文件的現有程式碼時，就會使用此功能。 換句話說，其中具有有限或不存在的程式碼規格。 它會有效地實作與 [Smart Unit Tests](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/19/introducing-smart-unit-tests.aspx) (智慧型單元測試) 類似的方法，以描述觀察到的程式碼行為。

不過，這項功能也同樣適用於這種情況；其中，開發人員會開始撰寫某個程式碼，並使用該程式碼來啟動單元測試專業領域。 在編碼流程內，開發人員可能想要快速建立特定程式碼部分的單元測試方法虛設常式 (具有適當的測試類別，以及適當的測試專案)。 

## <a name="more-information"></a>詳細資訊

請參閱部落格文章 [Creating unit test method stubs with "Create Unit Tests"](https://blogs.msdn.microsoft.com/visualstudioalm/2015/03/06/creating-unit-test-method-stubs-with-create-unit-tests/) (使用 [建立單元測試] 建立單元測試方法虛設常式)。

在[這裡](https://blogs.msdn.microsoft.com/visualstudioalm/tag/unit-testing/)可以找到更多單元測試部落格文章。
