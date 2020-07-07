---
title: 如何：將控制項標記為安全控制項 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd7ed13504d3d91f4239a8ea070454e1c31b1114
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016262"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>如何：將控制項標記為安全控制項
  基於安全性的關係，SharePoint 會區分保護不受腳本插入和 Web 控制項的 Web 控制項。 不受信任的使用者可以存取受保護的控制項或*安全控制項*。 當您將元件加入封裝時，可以在 SharePoint 專案專案的 [安全控制項專案] 屬性中，將控制項標示**為 [安全**]。 如需相關資訊，請參閱

- [web.config 檔案設定變更](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12))和[註冊 Web 元件元件，做為安全的控制項](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))。

> [!IMPORTANT]
> 這些程式僅供說明之用。 只有在您確定控制項安全時，才會將它們標示為安全。

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>在 [安全控制項專案] 屬性中標記安全控制項

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>若要在安全控制項專案屬性中將控制項標記為安全或不安全

1. 建立具有視覺化網頁元件專案的 SharePoint 方案。

2. 將兩個控制項加入至 Web 元件：一個文字方塊和一個按鈕。 將名稱分別保留為預設值（TextBox1 和 Button1）。

3. 將兩個專案加入至 Web 元件的 [**安全控制項專案**] 屬性。 若要這麼做，請選擇 [**屬性**] 視窗中 [**安全控制項專案**] 屬性旁的省略號（![ASP.NET Mobile 設計](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")工具省略號）按鈕。

     [**安全控制項專案**] 對話方塊隨即出現。

4. 在 [**安全控制項專案**] 對話方塊中，選擇 [**新增**] 按鈕兩次，將兩個安全控制項專案新增至 [**成員**] 窗格：一個用於按鈕，另一個用於文字方塊。

5. 選擇第一個安全控制項專案，然後將其 [**安全**] 屬性的值變更為 [ **false**]，其 [**類型名稱**] 屬性設為 [ **Button1**]，並將 [安全] [**針對腳本**] 屬性設為**false**。

     此步驟會將按鈕控制項識別為不安全的控制項。

6. 選擇清單中的第二個安全控制項項目。 將其 [**安全**] 屬性的值保留為 [ **true** ]，並將其 [**類型名稱**] 屬性**設定為 [** **TextBox1** ]，並將其 [安全] [**針對腳本**

     文字方塊控制項現在會標示為可安全地進行腳本插入的控制項。

7. 選擇 [確定]**** 按鈕以關閉對話方塊。

## <a name="marking-safe-controls-in-the-package-designer"></a>在封裝設計工具中標記安全控制項

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>若要在封裝設計工具中將控制項標記為安全或不安全

1. 建立具有視覺化網頁元件專案的 SharePoint 方案。

2. 將兩個控制項加入至 Web 元件：一個文字方塊和一個按鈕。 將名稱分別保留為預設值（TextBox1 和 Button1）。

     請記下控制項的命名空間，因為稍後會用到它。

3. 在功能表列上，選擇 [**組建**] [組建] [  >  **方案**] 來建立專案。

4. 建立另一個 SharePoint 方案。

5. 在**方案總管**中，開啟 [*封裝*檔案] 的快捷方式功能表，然後選擇 [**開啟**] 以開啟**封裝設計**工具。

6. 在**封裝設計**工具中，選擇 [ **Advanced** ] 索引標籤。

7. 在 [**其他元件**] 底下，選擇 [**加入**] 按鈕，然後從清單中選擇 [**加入現有元件**]。

8. 在 [**加入現有元件**] 對話方塊中，選擇 [**來源路徑**] 旁的省略號（![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")）按鈕。

9. 從您在步驟1中建立的 SharePoint 方案中選擇元件，然後選擇 [**開啟**] 按鈕。

10. 在此範例中，將 [**部署目標**] 選項保留為 [GlobalAssemblyCache]。

     此步驟會使元件部署到系統全域組件快取（GAC）。 如果您想要將元件部署至 Web 應用程式（Bin）資料夾，請改為選取該選項。 如需詳細資訊，請參閱[在 SharePoint Foundation 中部署 Web 組件](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))。

11. 在 [**安全控制項**] 方塊中，選擇 [**按一下這裡加入新專案**] 按鈕。

12. 輸入下表中的屬性值。

    |屬性名稱|值|
    |-------------------|-----------|
    |命名空間|控制項的完整命名空間，例如**BdcModelProject1. visualwebpartproject1.visualwebpart1.visualwebpart1**。|
    |類型名稱|Button1|
    |組件名稱|強式元件名稱，例如： ClientExtensions、Version = 14.0.0.0、Culture = 中性，PublicKeyToken = 71e9bce111e9429c。|
    |Safe|清除 [**安全**] 核取方塊。|
    |針對腳本安全|將 [不**受腳本**保護] 核取方塊保持為清除。|

    > [!NOTE]
    > 透過**封裝設計**工具的 [ **Advanced** ] 索引標籤加入之元件的**元件名稱**值不可以是 token，它必須是強式名稱的元件。 如需詳細資訊，請參閱[建立和使用強式名稱的組件](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100))。

13. 選擇**Tab**鍵以建立另一個安全控制項專案。

14. 再次選擇 [**按一下這裡加入新專案**] 按鈕。

15. 輸入下表中的屬性值。

    |屬性名稱|值|
    |-------------------|-----------|
    |命名空間|控制項的完整命名空間，例如**BdcModelProject1. visualwebpartproject1.visualwebpart1.visualwebpart1**。|
    |類型名稱|TextBox1|
    |組件名稱|強式元件名稱，例如： ClientExtensions、Version = 14.0.0.0、Culture = 中性，PublicKeyToken = 71e9bce111e9429c。|
    |Safe|選取 [**安全**] 核取方塊。|
    |針對腳本安全|選取 [**安全] [針對腳本**] 核取方塊。|

16. 選擇**Tab**鍵，然後選擇 [**確定**] 按鈕以關閉對話方塊。

## <a name="see-also"></a>另請參閱
- [提供專案專案中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
