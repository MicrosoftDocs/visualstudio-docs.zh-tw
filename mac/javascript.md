---
title: Javascript
description: Visual Studio for Mac 中的 Javascript 支援資訊
author: conceptdev
ms.author: crdun
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 21ff2211632cba63dafe2a7abf1964e7a89e87c3
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224169"
---
# <a name="javascript-support"></a>JavaScript 支援

Visual Studio for Mac 透過語法醒目提示、程式碼格式設定以及 IntelliSense 提供 Javascript 和 Typescript 支援。 

![typescript 編輯器支援](https://msdnshared.blob.core.windows.net/media/2018/03/TypeScript-editor.gif)

如需撰寫 JavaScript 的詳細資訊，請參閱[撰寫 Javascript 程式碼](https://docs.microsoft.com/scripting/javascript/writing-javascript-code)指南。

## <a name="adding-a-javascript-file"></a>新增 JavaScript 檔案

JavaScript 檔案最常透過 [新增檔案] 對話方塊新增至 ASP.NET Core 專案。 若要新增 javascript 檔案，請以滑鼠右鍵按一下您的專案，並移至 [新增] > [新增檔案]： 

![將新檔案新增至專案](media/javascript-image1.png)

從 [新增檔案] 對話方塊中，選取 [Web] > [空白 JS 檔案] 或 [Web] > [Typescript 檔案]。 指定名稱，然後選擇 [新增]：

![從範本建立新的 typescript 檔案](media/javascript-image2.png)

## <a name="intellisense"></a>Intellisense

Visual Studio for Mac 使用 [Javascript 語言服務](https://docs.microsoft.com/en-us/visualstudio/ide/javascript-intellisense) 提供 Intellisense，讓您撰寫程式碼時擁有智慧型程式碼完成功能、參數資訊和成員清單。

Visual Studio for Mac 中的 Javascript intellisense 可以基於型別推斷、JSDoc 或 Typescript 宣告。

- **型別推斷** – 藉由周圍的程式碼內容來判斷物件類型。 如需詳細資訊，請參閱 Visual Studio 的 [以型別推斷為基礎的 IntelliSense](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference) 一節。
- **JSDoc** – 有些時候型別推斷無法提供正確的類型資訊。 在此情況下，[JSDoc](http://usejsdoc.org/about-getting-started.html) 註解可以明確提供類型資訊。 如需詳細資訊，請參閱 Visual Studio 的 [以 JSDoc 為基礎的 IntelliSense](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc) 章節
- **TypeScript 宣告檔案** – `.d.ts` 檔案可用來為 Javascript Intellisense 提供值。 該檔案中宣告的類型可作為 JSDoc 註解之類型。 如需詳細資訊，請參閱 Visual Studio 的 [以 TypeScript 宣告檔案為基礎的 IntelliSense](https://docs.microsoft.com/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) 一節 ![新增 typescript 定義檔](media/javascript-image3.png)