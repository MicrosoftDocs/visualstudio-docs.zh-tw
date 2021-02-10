---
title: 如何：將控制項標記為安全控制項 |Microsoft Docs
description: 當您加入元件時，將控制項標記為 SharePoint 專案專案的 [安全控制項專案] 屬性或 [封裝設計工具] 中的安全控制項。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bf7e2f2c5b0de59a5f1cac91f0df9cefbf15bda8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964702"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>如何：將控制項標記為安全控制項
  基於安全性，SharePoint 會區分受保護的 Web 控制項與不是腳本插入的 web 控制項。 受信任的使用者可以存取受保護的控制項（或 *安全的控制項*）。 當您將元件加入封裝時，可以將控制項標示為 [安全控制項專案] 屬性中 SharePoint 專案專案或 **封裝設計** 工具中的控制項。 如需相關資訊，請參閱

- [web.config 檔案設定會變更](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) ，並將 [Web 元件元件註冊為安全控制項](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))。

> [!IMPORTANT]
> 這些程式是供說明之用。 只有當您確定控制項是安全的時，才會標示為安全的。

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>在 [安全控制項專案] 屬性中標示安全控制項

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>將控制項標示為安全或不安全的安全控制項專案屬性

1. 使用視覺網頁元件專案建立 SharePoint 方案。

2. 將兩個控制項新增至網頁元件：文字方塊和按鈕。 分別將名稱保留為預設值 TextBox1 和 Button1。

3. 將兩個專案加入至網頁元件的 **安全控制項專案** 屬性。 若要這樣做，請在 [**屬性**] 視窗中，選擇 [**安全控制項專案**] 屬性旁的省略號 (![ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")省略號) 按鈕。

     [ **安全控制項專案** ] 對話方塊隨即出現。

4. 在 [ **安全控制項專案** ] 對話方塊中，選擇 [ **加入** ] 按鈕兩次，將兩個安全控制項專案加入至 [ **成員** ] 窗格：一個用於按鈕，另一個用於文字方塊。

5. 選擇第一個安全控制項專案，然後將其 [ **安全** ] 屬性的值變更為 [ **false**]，將其 [ **類型名稱** ] 屬性變更為 [ **Button1**]，並將 [ **對腳本的安全** ] 屬性變更為 **false**。

     此步驟會將按鈕控制項識別為不安全的控制項。

6. 選擇清單中的第二個安全控制項項目。 將其 [ **安全** ] 屬性的值保留為 **true** ，並將其 [ **類型名稱** ] 屬性設定為 [ **TextBox1** ]，並將 [ **針對腳本** ] 屬性設定為 **true**。

     文字方塊控制項現在會標示為可安全地對腳本插入的控制項。

7. 選擇 [確定] 按鈕以關閉對話方塊。

## <a name="marking-safe-controls-in-the-package-designer"></a>在封裝設計工具中標示安全控制項

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>將控制項標記為安全或不安全的封裝設計工具

1. 使用視覺網頁元件專案建立 SharePoint 方案。

2. 將兩個控制項新增至網頁元件：文字方塊和按鈕。 分別將名稱保留為預設值 TextBox1 和 Button1。

     記下控制項的命名空間，因為稍後會用到它。

3. 在功能表列上，選擇 [**組建**  >  **組建方案**] 以建立專案。

4. 建立另一個 SharePoint 方案。

5. 在 **方案總管** 中，開啟 [ *封裝* 檔案] 的快捷方式功能表，然後選擇 [ **開啟** ] 以開啟 **封裝設計** 工具。

6. 在 **封裝設計** 工具中，選擇 [ **Advanced** ] 索引標籤。

7. 在 [ **其他元件**] 下，選擇 [ **加入** ] 按鈕，然後從清單中選擇 [ **加入現有的元件** ]。

8. 在 [**加入現有元件**] 對話方塊中，選擇 [**來源路徑**] 旁的省略號 (![ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")省略號) 按鈕。

9. 從您在步驟1建立的 SharePoint 方案中選擇元件，然後選擇 [ **開啟** ] 按鈕。

10. 在此範例中，將 [ **部署目標** ] 選項保留為 [GlobalAssemblyCache]。

     此步驟會使元件部署至系統全域組件快取 (GAC) 。 如果您想要將元件部署至 Web 應用程式 (Bin) 資料夾，請改為選取該選項。 如需詳細資訊，請參閱 [在 SharePoint Foundation 中部署 Web 組件](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))。

11. 在 [ **安全控制項** ] 方塊中，選擇 [ **按一下這裡加入新專案** ] 按鈕。

12. 輸入下表中的屬性值。

    |屬性名稱|值|
    |-------------------|-----------|
    |命名空間|控制項的完整命名空間，例如 **BdcModelProject1. VisualWebPart1**。|
    |類型名稱|Button1|
    |組件名稱|強式元件名稱，例如： ClientExtensions、Version = 14.0.0.0、Culture = 中立、PublicKeyToken = 71e9bce111e9429c。|
    |保險箱|清除 [ **安全** ] 核取方塊。|
    |安全地對抗腳本|將 [ **對腳本保持安全** ] 核取方塊保持為清除。|

    > [!NOTE]
    > 透過 **封裝設計** 工具的 [ **Advanced** ] 索引標籤加入的元件的 **元件名稱** 值不能是標記，它必須是強式名稱的元件。 如需詳細資訊，請參閱[建立和使用強式名稱的組件](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100))。

13. 選擇 **Tab** 鍵以建立另一個安全控制項專案。

14. 選擇 [ **按一下這裡加入新專案** ] 按鈕。

15. 輸入下表中的屬性值。

    |屬性名稱|值|
    |-------------------|-----------|
    |命名空間|控制項的完整命名空間，例如 **BdcModelProject1. VisualWebPart1**。|
    |類型名稱|TextBox1|
    |組件名稱|強式元件名稱，例如： ClientExtensions、Version = 14.0.0.0、Culture = 中立、PublicKeyToken = 71e9bce111e9429c。|
    |保險箱|選取 [ **安全** ] 核取方塊。|
    |安全地對抗腳本|選取 [ **安全地針對腳本** ] 核取方塊。|

16. 選擇 **Tab** 鍵，然後選擇 [ **確定** ] 按鈕以關閉對話方塊。

## <a name="see-also"></a>另請參閱
- [提供專案專案中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
