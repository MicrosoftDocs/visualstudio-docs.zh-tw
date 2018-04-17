---
title: 如何： 將控制項標記為安全控制項 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d703beb24821663b08ed69238fcf27e2a752d64b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-mark-controls-as-safe-controls"></a>如何：將控制項標記為安全控制項
  為了安全性，SharePoint 會區別 Web 指令碼資料隱碼對受保護的 Web 控制項，以及不是。 受保護的控制項，或*安全控制項*，可以由不受信任的使用者存取。 您可以將標記為安全的安全控制項項目屬性，SharePoint 專案項目，或在中的控制項**封裝設計工具**將組件加入封裝。 如需詳細資訊，請參閱  
  
 [web.config 檔案設定變更](http://go.microsoft.com/fwlink/?LinkId=178965)和[Web 組件登錄成安全控制](http://go.microsoft.com/fwlink/?LinkId=171013)。  
  
> [!IMPORTANT]  
>  這些程序是為了說明之用。 只有在確定它們都是安全的安全控制項標記。  
  
## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>標示安全控制項項目屬性中的安全控制項  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>若要將標示為安全 safe 或 unsafe 安全控制項項目屬性中的控制項  
  
1.  使用視覺 Web 組件的專案中建立 SharePoint 方案。  
  
2.  將兩個控制項加入至 Web 組件： 文字方塊和按鈕。 分別保留這些名稱在 TextBox1 和 Button1，其預設值。  
  
3.  將兩個項目加入至 Web 組件的**安全控制項項目**屬性。 若要這樣做，請選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 旁邊**安全控制項項目**屬性**屬性**視窗。  
  
     **安全控制項項目** 對話方塊隨即出現。  
  
4.  在**安全控制項項目**對話方塊方塊中，選擇**新增**按鈕兩次，新增兩個安全控制項項目至**成員**窗格： 其中一個按鈕和一個文字方塊。  
  
5.  選擇第一個安全控制項項目，然後再將值變更其**安全**屬性**False**、 其**型別名稱**屬性**Button1**，且其**防止指令碼**屬性**False**。  
  
     此步驟會識別為不安全的控制項的按鈕控制項。  
  
6.  選擇清單中的第二個安全控制項項目。 保留值其**安全**屬性做為**True**並設定其**型別名稱**屬性**TextBox1**及其**安全針對指令碼**屬性**True**。  
  
     文字方塊控制項現在會標示為安全針對指令碼資料隱碼的控制項。  
  
7.  選擇 [確定] 按鈕以關閉對話方塊。  
  
## <a name="marking-safe-controls-in-the-package-designer"></a>標示在封裝設計工具中的安全控制項  
  
#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>若要將標示控制項為安全 safe 或 unsafe 封裝設計工具中  
  
1.  使用視覺 Web 組件的專案中建立 SharePoint 方案。  
  
2.  將兩個控制項加入至 Web 組件： 文字方塊和按鈕。 分別保留這些名稱在 TextBox1 和 Button1，其預設值。  
  
     記下的控制項的命名空間之後，它會用。  
  
3.  在功能表列上選擇 **建置**，**建置方案**建置專案。  
  
4.  建立另一個 SharePoint 方案。  
  
5.  在**方案總管 中**，開啟 Package.Package 檔案、 捷徑功能表，然後選擇**開啟**開啟**封裝設計工具**。  
  
6.  在**封裝設計工具**，選擇**進階** 索引標籤。  
  
7.  在下**其他組件**，選擇**新增**按鈕，然後再選擇**加入現有的組件**從清單中。  
  
8.  在**加入現有的組件**對話方塊方塊中，選擇省略符號 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 旁邊**來源路徑**。  
  
9. 選擇您在步驟 1 中建立 SharePoint 方案的組件，然後選擇**開啟** 按鈕。  
  
10. 此範例中，將保留**部署目標**為 GlobalAssemblyCache 選項。  
  
     這個步驟會導致將部署至系統全域組件快取 (GAC) 組件。 如果您想要部署至 Web 應用程式 (Bin) 資料夾的組件，請改為選取該選項。 如需詳細資訊，請參閱[部署在 SharePoint Foundation 中的 Web 組件](http://go.microsoft.com/fwlink/?LinkId=177509)。  
  
11. 在**安全控制項**方塊中，選擇**按一下此處以加入新項目** 按鈕。  
  
12. 下表中輸入屬性的值。  
  
    |屬性名稱|值|  
    |-------------------|-----------|  
    |命名空間|控制項的完整命名空間這類**BdcModelProject1.VisualWebPart1**。|  
    |類型名稱|Button1|  
    |組件名稱|強式組件名稱，例如： Microsoft.Office.SharePoint.ClientExtensions，Version = 版本為 14.0.0.0，Culture = neutral，PublicKeyToken = 71e9bce111e9429c。|  
    |安全|清除**安全**核取方塊。|  
    |針對指令碼的安全|保留**防止指令碼**清除核取方塊。|  
  
    > [!NOTE]  
    >  **組件名稱**透過加入的組件的值**進階** 索引標籤**封裝設計工具**不能是語彙基元，它必須是具備強式名稱組件。 如需詳細資訊，請參閱[建立和使用強式名稱的組件](http://go.microsoft.com/fwlink/?LinkId=177513)。  
  
13. 選擇 Tab 鍵建立另一個安全控制項項目。  
  
14. 選擇**按一下此處以加入新項目**按鈕一次。  
  
15. 下表中輸入屬性的值。  
  
    |屬性名稱|值|  
    |-------------------|-----------|  
    |命名空間|控制項的完整命名空間這類**BdcModelProject1.VisualWebPart1**。|  
    |類型名稱|TextBox1|  
    |組件名稱|強式組件名稱，例如： Microsoft.Office.SharePoint.ClientExtensions，Version = 版本為 14.0.0.0，Culture = neutral，PublicKeyToken = 71e9bce111e9429c。|  
    |安全|選取**安全**核取方塊。|  
    |針對指令碼的安全|選取**防止指令碼**核取方塊。|  
  
16. 選擇 Tab 鍵，然後再選擇**確定**按鈕以關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [提供封裝和專案項目中的部署資訊](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  