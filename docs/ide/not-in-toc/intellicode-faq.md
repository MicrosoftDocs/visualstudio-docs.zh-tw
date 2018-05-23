---
title: IntelliCode 常見問題集
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: df5ce60e9d7a05d8cc7c9ebbe173dd30a0a0edf4
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2018
---
# Visual Studio IntelliCode 常見問題集

感謝您對 Visual Studio IntelliCode 的關注！ 我們提供此簡短的常見問題集，希望能夠回答您可能遇到的一些問題。

## 問： 什麼是 Visual Studio IntelliCode？

在 2018 組建中，我們宣告了 Visual Studio IntelliCode，其為一種使用 AI 來增強軟體開發的新功能。 IntelliCode 可幫助開發人員及小組有自信地編碼、更快地發現問題、專注於程式碼檢閱。

我們也示範了 IntelliCode 如何以下列方式增強軟體開發過程的早期檢視：

- 提供內容感知程式碼完成
- 引導開發人員遵守所屬小組的模式與風格
- 發現難以捕捉的程式碼問題
- 透過將注意力放在真正重要的區域，從而專注於程式碼檢閱

開發人員可以在 [https://aka.ms/intellicode](https://aka.ms/intellicode) 取得更多資訊，並註冊相關新聞與未來的個人預覽版。

## 問： Visual Studio IntelliCode 可以讓客戶做些什麼？

Visual Studio IntelliCode 具一系列功能，可通過人工智慧 (AI) 提供新的生產力增強功能。

開發人員可以針對 Visual Studio 2017 15.7 和更新版本[下載實驗性延伸模組](https://go.microsoft.com/fwlink/?linkid=872707)。 延伸模組提供增強的 IntelliSense，可預測最可能正確的 API 給開發人員使用，而不僅僅是按字母順序排列來呈現成員清單。 會使用開發人員的目前程式碼內容和模式，以提供動態清單。 接下來的幾個月，我們會以更多功能來更新延伸模組。

## 問：由 IntelliCode 提供的「AI 輔助 IntelliSense」優於一般的 IntelliSense 要素為何？

使用 IntelliCode，完成清單可為開發人員提供最可能正確的 API，而不僅僅是按字母順序排列來呈現成員清單。 會使用開發人員目前的程式碼內容，以及基於 GitHub 上 2000 個高品質開放來源專案 (每個皆超過 100 顆星) 的模式，來提供此動態清單。 結果會形成一個能預測最可能和最相關之 API 呼叫的模型。

## Q：IntelliCode 完成建議好用嗎？

雖然最後還是得取決這些建議在您編碼時的實用度， 但我們已經在 Microsoft 內部使用 IntelliCode 的建議一段時間了，並認為這些建議很實用。 我們希望您給 Visual Studio [IntelliCode 延伸模組](https://go.microsoft.com/fwlink/?linkid=872707)一個機會。 請讓我們了解您的使用情形，並傳送意見反應給我們。 我們也會根據您在建議中挑選的項目來訓練模型，並在模型改善時更新延伸模組。

> [!NOTE]
> 我們並不會收集任何使用者定義的程式碼。 請參閱[隱私權](#privacy)上的問題。

## 問： IntelliCode 的未來是什麼？

我們正在探索使用 AI 和其他先進技術來提高開發人員生產力的各種方法。 在 2018 組建中，我們示範了一些我們認為 AI 能幫助開發人員之案例的早期檢視，但還有更多其他的！ 對於開發人員使用我們示範的內容來進行之實驗，我們有興趣了解，請在 [https://aka.ms/intellicode](https://aka.ms/intellicode) 註冊相關新聞與更新。

## 問： 費用是多少？

目前我們沒有關於定價的公告。

## 問： 何時會發行 IntelliCode？

IntelliCode 的 AI 輔助 IntelliSense 目前為第一個實驗性預覽版本。 我們會持續更新實驗性延伸模組，未來將進一步新增功能。 我們沒有最終版本的發行時間表，但我們歡迎來自開發人員的意見反應，幫助我們提供最佳的體驗。 您可以在 [https://aka.ms/intellicode](https://aka.ms/intellicode) 註冊相關新聞與更新。

## 問： 這項體驗只能在 Visual Studio 中以 C# 使用嗎？

在 C# 程式碼基底之 Visual Studio 2017 中的 2018 組建中已示範體驗。 但是，我們期待未來將 IntelliCode 擴展到 Visual Studio 系列的更多語言和工具中。

## 問： 我需要哪個版本的 Visual Studio 才能執行此延伸模組？

Visual Studio 2017 15.7 版 Preview 5 和更新版本 (所有 SKU) 均支援 Visual Studio IntelliCode 延伸模組。 如果您未安裝最低需求的版本， 那麼延伸模組的安裝會停止並出現「此延伸模組並不適用於任何目前安裝的產品。」

## 問： 這項體驗只提供英文版嗎？

IntelliCode 目前是預覽延伸模組，我們相當希望了解這些功能對我們廣泛的客群而言有多麼實用。 當我們結束 IntelliCode 的預覽階段後，必定會根據您的意見反應來考量應該優先支援哪些語言，以及支援套件的封裝方式。 

## <a name="privacy"/> Q：隱私權方面呢？ 是否會將我的程式碼傳送到雲端？ 哪些客戶資料會傳送給 Microsoft？

我們邀請開發人員體驗 Visual Studio IntelliCode 作為實驗性預覽版本延伸模組。 延伸模組的目的是使開發人員能夠測試 IntelliCode 功能並向產品小組提供意見反應。

我們從延伸模組中擷取一些匿名的使用方式和錯誤報告資料，以幫助改善產品。 沒有任何使用者定義的程式碼會傳送給 Microsoft，但我們會收集您使用 IntelliCode 結果的相關資訊。 資料只會包含您從 IntelliCode 建議清單中選擇的開放來源和 .NET 類型與成員。 開發人員可以選擇退出 Visual Studio 資料收集，這也會關閉 IntelliCode 延伸模組的資料收集。 從功能表列中，選取 [協助] > [傳送意見反應] > [設定]。 在 [Visual Studio 經驗改進計畫] 對話方塊中，選取 [否，我不願意參與]，然後選取 [確定]。

IntelliCode 延伸模組可能會定期要求開發人員完成一份問卷調查，該調查也是匿名的。 使用者可以註冊相關新聞和未來的個人預覽版，但目前不需要這麼做，即可使用實驗性延伸模組。

未來的功能可能將需要註冊以取得服務的存取權。 當個人預覽版已準備好這些功能時，我們將發佈更多詳細資料。
