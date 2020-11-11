---
title: 管理專案和方案屬性
description: 本文說明如何在 Visual Studio for Mac 中管理專案和方案的屬性。
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 0c3277df3be22658acf85a4f0607ed9ad0308b5c
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492993"
---
# <a name="managing-project-and-solution-properties"></a>管理專案和方案屬性

## <a name="project-options"></a>專案選項

專案選項專屬於每個專案，並影響如何撰寫、建置和執行專案。 不同于使用者特定設定 Visual Studio for Mac 喜好設定，專案選項會儲存在專案 ( .csproj) 檔中，讓其他開發人員可以正確地建立及執行專案。 使用特定專案選項可讓多個開發人員處理相同的文件，而不影響檔案格式。

若要在 Visual Studio for Mac 中開啟專案選項，請按兩下專案名稱，或以滑鼠右鍵按一下以開啟操作功能表，然後選取 [選項]：

![操作功能表中的選項](media/projects-and-solutions-image2.png)

可編輯的選項包含建置、執行以及設定原始程式碼和版本控制的選項。

專案選項會組織成五個不同的類別：

* **一般** - 您會在這裡設定 [名稱]、[描述] 和 [預設命名空間] 等專案資訊，以及專案的 [位置]。
* **Build** -用來設定或變更可移植類別庫的 PCL 設定檔。 它也允許自訂命令、組態、要設定的編譯器選項。 您也可以在這裡設定輸出路徑和組件名稱。
* **執行** -用來針對每個專案建立自訂執行設定。
* **原始程式碼** -控制許多不同檔案類型和命名慣例的格式。 您也可以在這裡設定命名原則和預設標頭樣式。
* **版本控制** -在您的專案中使用版本控制時，設定認可訊息樣式的選項。

每個專案都可以包含特定的專案選項 (視平台而定)。 例如，下圖中所述 Xamarin.Android 專案會有與 Android 組建相關的選項 (例如連結器選項)，以及與應用程式相關的選項 (例如權限)：

![Android 專案選項](media/projects-and-solutions-image5.png)

Xamarin.iOS 具有與套件組合簽署相關的選項，例如要使用的必要佈建設定檔：

![iOS 專案選項](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>方案選項

方案選項就像專案選項，但涵蓋整個方案的範圍。 它們提供方法來設定作者資訊、組建設定、程式碼格式樣式和版本控制，並且允許在方案中指派啟始專案的方法。  您可以從 **> 專案** 的 [方案選項] 功能表項目、方案視窗中方案的 [ **選項** ] 內容功能表項目，或在 [方案] 視窗中按兩下方案，來存取 [方案選項] 對話方塊：

![方案選項](media/projects-and-solutions-image7.png)

## <a name="see-also"></a>請參閱

* [管理專案和方案屬性 (Windows 上的 Visual Studio)](/visualstudio/ide/managing-project-and-solution-properties)