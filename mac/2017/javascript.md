---
title: JavaScript 和 TypeScript
description: Visual Studio for Mac 中 Javascript 支援的相關資訊
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/03/2018
ms.technology: vs-ide-general
ms.assetid: 61432695-5B12-4257-B250-48D37EED106D
ms.openlocfilehash: 5f1a400506f7766ba22ffbc1debde687b1709a21
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760922"
---
# <a name="javascript-and-typescript-support"></a>JavaScript 和 TypeScript 支援

Visual Studio for Mac 透過語法醒目提示、程式碼格式化以及 IntelliSense，來提供 JavaScript 和 TypeScript 的支援。

![typescript 編輯器支援](/visualstudio/mac/media/tsjseditor-2019.gif)

如需撰寫 JavaScript 的詳細資訊，請參閱 [Writing JavaScript Code](/scripting/javascript/writing-javascript-code) (撰寫 Javascript 程式碼) 指南。

## <a name="adding-a-javascript-file"></a>新增 JavaScript 檔案

JavaScript 檔案最常透過 [新增檔案] 對話方塊新增至 ASP.NET Core 專案。 若要新增 javascript 檔案，請以滑鼠右鍵按一下您的專案，並移至 [新增] > [新增檔案]：

![將新檔案新增至專案](media/javascript-image1.png)

從 [新增檔案] 對話方塊中，選取 [Web] > [空白 JS 檔案] 或 [Web] > [TypeScript 檔案]。 指定名稱，然後選擇 [新增]：

![從範本建立新的 typescript 檔案](media/javascript-image2.png)

## <a name="intellisense"></a>IntelliSense

Visual Studio for Mac 使用 [JavaScript Language Service](/visualstudio/ide/javascript-intellisense) 來提供 IntelliSense，讓您撰寫程式碼時，可擁有智慧型程式碼完成功能、參數資訊和成員清單。

Visual Studio for Mac 中的 Javascript intellisense 可以型別推斷、JSDoc 或 TypeScript 宣告為依據。

- **型別推斷** – 藉由周圍的程式碼內容來判斷物件類型。 如需詳細資訊，請參閱 Visual Studio 的 [以型別推斷為基礎的 IntelliSense](/visualstudio/ide/javascript-intellisense#intellisense-based-on-type-inference) 一節。
- **JSDoc** – 有些時候型別推斷無法提供正確的類型資訊。 在此情況下，[JSDoc](https://jsdoc.app/about-getting-started.html) 註解可以明確提供類型資訊。 如需詳細資訊，請參閱 Visual Studio 的 [以 JSDoc 為基礎的 IntelliSense](/visualstudio/ide/javascript-intellisense#intellisense-based-on-jsdoc) 一節
- **TypeScript** 宣告檔–檔案 `.d.ts` 是用來提供 JavaScript IntelliSense 的值。 該檔案中宣告的類型可作為 JSDoc 註解之類型。 如需詳細資訊，請參閱 Visual Studio 的[以 TypeScript 宣告檔案為基礎的 IntelliSense](/visualstudio/ide/javascript-intellisense#intellisense-based-on-typescript-declaration-files) 一節

    ![新增 TypeScript 定義檔](media/javascript-image3.png)

## <a name="see-also"></a>另請參閱

- [JavaScript IntelliSense (Windows 上的 Visual Studio)](/visualstudio/ide/javascript-intellisense)
