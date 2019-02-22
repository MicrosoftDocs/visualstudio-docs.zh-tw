---
title: 重新整理的 UWP 應用程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 0baa9e9a94b96682cda21dec9a5ba76cbe7f0065
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970912"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>重新整理 Visual Studio 中的 UWP 應用程式
  
 您可以進行變更您的程式碼，而您在偵錯，然後重新整理選擇使用 JavaScript 的 UWP 應用程式**重新整理 Windows 應用程式**按鈕**偵錯**工具列。 選擇此按鈕隨即會重新載入應用程式，而不需要停止並重新開始偵錯工具。 重新整理功能可讓您修改 HTML、CSS 和 JavaScript 程式碼，並且快速查看結果。 這項功能被支援 UWP 應用程式。  
  
 重新整理不會維護您的應用程式狀態，也不會將下列變更反映給應用程式：  
  
-   封裝資訊清單檔案變更，包括對封裝資訊清單中指定之影像的變更。  
  
-   參考變更 (例如新增或移除 SDK 參考)，或者對 Windows 執行階段元件 (.winmd 檔案) 的變更。  
  
-   資源變更，例如對 .resjson 檔案中字串的變更。  
  
-   專案檔案變更，該變更導致路徑名稱變更、新增專案檔案或刪除檔案。  
  
-   專案和項目屬性變更，例如對選取之偵錯裝置的變更，或對檔案之封裝動作的變更 (在 [屬性] 視窗中)。  
  
> [!IMPORTANT]
>  當您變更參考、封裝資訊清單或進行前述清單中指定的其他變更時，必須停止然後重新啟動偵錯工具才能更新 HTML、CSS 和 JavaScript 原始程式檔。  
  
### <a name="to-refresh-an-app"></a>若要重新整理應用程式  
  
1.  在 Visual Studio 中開啟 UWP 專案，選取**本機電腦**做為偵錯目標。
  
     ![選取偵錯目標清單](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  請按 F5 以偵錯模式執行應用程式。  
  
4.  切換至 Visual Studio。 
  
5.  在 UWP 應用程式的首頁上，編輯部分的 html。
  
7.  按一下 [重新整理 Windows 應用程式 **按鈕，如下所示：**![重新整理 Windows 應用程式] 按鈕](../debugger/media/js_refresh.png "JS_Refresh")。 (或按 F4)。  
  
8.  切換至應用程式。 應用程式會重新載入，並用來呈現應用程式更新的 HTML。
  
## <a name="see-also"></a>請參閱  
 [快速入門：對 HTML 和 CSS 進行偵錯](../debugger/quickstart-debug-html-and-css.md)