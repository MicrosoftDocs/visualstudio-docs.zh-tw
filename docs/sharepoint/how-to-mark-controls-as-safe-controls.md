---
title: HOW TO：將控制項標記為安全控制項 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 0d2dfe0da64abb9540724c05d13b84715a684af0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60082031"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>HOW TO：將控制項標記為安全控制項
  為了安全性，SharePoint 會區別指令碼資料隱碼攻擊時受到保護的 Web 控制項和 Web 控制項不是。 受保護的控制項，或是*安全控制項*，可以由不受信任的使用者存取。 您可以將標記為安全的 SharePoint 專案項目，或在 安全控制項項目屬性中的控制項**封裝設計工具**將組件加入封裝。 如需詳細資訊，請參閱

- [web.config 檔案設定變更](http://go.microsoft.com/fwlink/?LinkId=178965)並[Web 組件註冊為安全控制項](http://go.microsoft.com/fwlink/?LinkId=171013)。

> [!IMPORTANT]
>  這些程序是為了說明之用。 只有當確定它們是安全的安全控制項標記。

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>標示的安全控制項項目屬性中的安全控制項

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>若要將控制項標示為 safe 或 unsafe 安全控制項項目屬性

1. 建立 SharePoint 解決方案與視覺 Web 組件專案。

2. 將兩個控制項新增至網頁組件： 文字方塊和按鈕。 分別在其預設值，TextBox1 與 Button1，保留這些名稱。

3. 將兩個項目新增至 Web 組件的**安全控制項項目**屬性。 若要這樣做，請選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 按鈕旁**安全控制項項目**中的屬性**屬性**視窗。

     **安全控制項項目** 對話方塊隨即出現。

4. 在**安全控制項項目**對話方塊方塊中，選擇**新增**按鈕兩次，兩個安全控制項項目新增至**成員**窗格： 其中一個按鈕和一個文字方塊。

5. 選擇第一個安全控制項項目，然後變更 值及其**安全**屬性設**False**、 其**型別名稱**屬性設**Button1**，並將其**防止指令碼**屬性設**False**。

     此步驟中識別為不安全的控制項的按鈕控制項。

6. 選擇清單中的第二個安全控制項項目。 保留值其**安全**屬性設為 **，則為 True**並設定其**型別名稱**屬性設**TextBox1**及其**安全針對指令碼**屬性，以 **，則為 True**。

     文字方塊控制項現在會標示為安全對指令碼資料隱碼攻擊的控制項。

7. 選擇 [確定] 按鈕以關閉對話方塊。

## <a name="marking-safe-controls-in-the-package-designer"></a>將標記在封裝設計工具中的安全控制項

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>若要將標記控制為 safe 或 unsafe 在封裝設計工具

1. 建立 SharePoint 解決方案與視覺 Web 組件專案。

2. 將兩個控制項新增至網頁組件： 文字方塊和按鈕。 分別在其預設值，TextBox1 與 Button1，保留這些名稱。

     記下此控制項的命名空間以便稍後使用。

3. 在功能表列上選擇 **建置** > **建置方案**來建置專案。

4. 建立另一個 SharePoint 方案。

5. 在 **方案總管 中**，開啟捷徑功能表*封裝*檔案，然後再選擇 **開啟**以開啟**封裝設計工具**.

6. 在 [ **Package Designer**，選擇**進階**] 索引標籤。

7. 底下**其他組件**，選擇**新增**按鈕，然後再選擇**加入現有組件**從清單中。

8. 在 **加入現有組件**對話方塊方塊中，選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 按鈕旁**來源路徑**。

9. 選擇從您在步驟 1 中建立 SharePoint 方案的組件，然後選擇**開啟** 按鈕。

10. 此範例中，保持**部署目標**GlobalAssemblyCache 選項。

     這個步驟會導致要部署到系統全域組件快取 (GAC) 的組件。 如果您想要部署至 Web 應用程式 (Bin) 資料夾的組件，請改為選取該選項。 如需詳細資訊，請參閱 <<c0> [ 部署 SharePoint Foundation 中的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=177509)。

11. 在 [**安全控制項**方塊中，選擇**按一下這裡以加入新項目**] 按鈕。

12. 下表中輸入屬性的值。

    |屬性名稱|值|
    |-------------------|-----------|
    |命名空間|控制項的完整命名空間這類**BdcModelProject1.VisualWebPart1**。|
    |類型名稱|Button1|
    |組件名稱|強式的組件名稱，例如：Microsoft.Office.SharePoint.ClientExtensions，version=14.0.0.0，Culture = neutral，PublicKeyToken = 71e9bce111e9429c。|
    |安全|清除**安全**核取方塊。|
    |針對指令碼的安全|離開**防止指令碼**清除核取方塊。|

    > [!NOTE]
    >  **組件名稱**值，透過新增的組件**進階**索引標籤**封裝設計工具**不能是語彙基元，它必須是強式名稱組件。 如需詳細資訊，請參閱[建立和使用強式名稱的組件](http://go.microsoft.com/fwlink/?LinkId=177513)。

13. 選擇** 索引標籤**金鑰，才能建立另一個安全控制項項目。

14. 選擇**按一下這裡以加入新項目**按鈕一次。

15. 下表中輸入屬性的值。

    |屬性名稱|值|
    |-------------------|-----------|
    |命名空間|控制項的完整命名空間這類**BdcModelProject1.VisualWebPart1**。|
    |類型名稱|TextBox1|
    |組件名稱|強式的組件名稱，例如：Microsoft.Office.SharePoint.ClientExtensions，version=14.0.0.0，Culture = neutral，PublicKeyToken = 71e9bce111e9429c。|
    |安全|選取 **安全**核取方塊。|
    |針對指令碼的安全|選取 **防止指令碼**核取方塊。|

16. 選擇** 索引標籤**鍵，然後再選擇**確定**按鈕以關閉對話方塊。

## <a name="see-also"></a>另請參閱
- [提供專案項目中的封裝和部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
