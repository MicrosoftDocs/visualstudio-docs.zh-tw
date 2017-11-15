---
title: "管理專案和方案屬性 | Microsoft Docs"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 8871ab002a94a9c0bbc0063a25b4dea9cb271142
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="managing-project-and-solution-properties"></a>管理專案和方案屬性

## <a name="project-options"></a>專案選項

專案選項專屬於每個專案，並影響如何撰寫、建置和執行專案。 這對照於 Visual Studio for Mac 喜好設定 (其設定使用者特有選項) 以及方案選項 (其設定整個方案的選項)。 專案選項儲存在專案 (.csproj) 檔案中，讓其他開發人員可以正確地建置和執行專案。 這可讓多位開發人員處理相同的文件，而不影響檔案格式。

Visual Studio for Mac 中專案選項的啟動方式是按兩下專案名稱，或按一下滑鼠右鍵以開啟操作功能表，並選取 [選項]：

 ![操作功能表中的選項](media/projects-and-solutions-image2.png)

可編輯的選項包含建置、執行以及設定原始程式碼和版本控制選項的選項。

專案選項會組織成五個具有下列功能的不同類別：

* **一般** - 您可以在這裡設定「名稱」、「描述」和「預設命名空間」這類專案資訊，以及專案的位置。
* **建置** - 這可讓開發人員設定或變更可攜式類別庫的 PCL 設定檔。 它也允許自訂命令、組態、要設定的編譯器選項。 您也可以在這裡設定輸出路徑和組件名稱。
* **執行** - 這可讓您根據每個專案來建立自訂回合組態。
* **原始程式碼** - 這可讓您控制許多不同檔案類型和命名慣例的格式。 您也可以在這裡設定命名原則和預設標頭樣式。
* **版本控制** - 這可讓您搭配使用 [版本控制] 與專案來編輯認可訊息的樣式。

每個專案也可以包含特定專案選項 (視平台而定)。 例如，下圖所述的 Xamarin.Android 專案會有 Android 組建相關選項 (例如連結器選項) 以及應用程式 (例如權限)：

 ![Android 專案選項](media/projects-and-solutions-image5.png)

Xamarin.iOS 將包含套件組合簽署相關選項 (例如要使用的必要佈建設定檔) 以及相關 IPA 封裝選項：

 ![iOS 專案選項](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>方案選項 

方案選項就像專案選項，但涵蓋整個方案的範圍。 它們提供方法來設定作者資訊、組建設定、程式碼格式樣式和版本控制，並且允許在方案中指派啟始專案的方法。  從 [專案] > [解決方案選項] 功能表項目、從 Solution Pad [解決方案] 上的 [選項] 操作功能表項目，或按兩下 Solution Pad 中的 [解決方案]，即可存取 [解決方案選項] 對話方塊：

 ![方案選項](media/projects-and-solutions-image7.png)
