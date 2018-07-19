---
title: 建立實體之間的關聯 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 22ac00ac48f4fe907e4fb4215992b49227f39961
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325459"
---
# <a name="create-an-association-between-entities"></a>建立實體之間的關聯
  您可以定義您藉由建立關聯的商務資料連接 (BDC) 模型中實體之間的關聯性。 Visual Studio 會產生模型的取用者提供每一個關聯的相關資訊的方法。 這些方法可以由 SharePoint Web 組件、清單或自訂應用程式加以使用，以便在使用者介面 (UI) 中顯示資料關聯性。  
  
## <a name="create-an-association"></a>建立關聯
 選擇 建立關聯**關聯**Visual Studio 中的控制**工具箱**，選擇第一個實體 （稱為來源實體），然後選擇 第二個實體 (稱為目的地實體）。 您可以定義中的關聯的詳細資料**關聯編輯器**。 如需詳細資訊，請參閱 <<c0> [ 如何： 建立實體之間的關聯](../sharepoint/how-to-create-an-association-between-entities.md)。  
  
## <a name="association-methods"></a>關聯方法
 應用程式，例如 SharePoint 商務資料 web 組件會使用關聯實體的服務類別中呼叫方法。 您可以將方法加入至實體的服務類別，請選取圖形中**關聯編輯器**。  
  
 根據預設，**關聯編輯器**關聯巡覽方法將來源和目的地實體。 來源實體中的關聯巡覽方法讓消費者可以擷取目的地實體的清單。 在 目的地實體的關聯巡覽方法讓消費者可以擷取目的地實體與相關來源實體。  
  
 您必須將程式碼新增至每一種方法來傳回適當的資訊。 您也可以新增其他類型的方法，以支援更進階的案例。 如需每一種方法的詳細資訊，請參閱[支援的作業](http://go.microsoft.com/fwlink/?LinkId=169286)。  
  
## <a name="types-of-associations"></a>類型的關聯
 您可以在 BDC 設計工具中建立關聯的兩種： 外部索引鍵為基礎的關聯和外部無索引鍵的關聯。  
  
### <a name="foreign-key-based-association"></a>外部索引鍵為基礎的關聯
 您可以建立外部索引鍵為基礎的關聯相關來源實體，輸入目的地實體中定義的描述元中的識別項。 此關聯性可讓模型的取用者為其使用者提供增強的 UI。 例如，可讓使用者建立可以在下拉式清單中顯示客戶的銷售訂單的 outlook 表單或在 SharePoint 中，可讓使用者開啟設定檔頁面，為客戶的銷售訂單的清單。  
  
 若要建立外部索引鍵為基礎的關聯，與相關的識別項，並輸入共用相同的名稱和類型的描述元。 例如，您可以在其中建立外部索引鍵為基礎的關聯之間`Contact`實體和`SalesOrder`實體。 `SalesOrder`實體傳回`ContactID`一部分傳回的搜尋工具 」 或 「 特定搜尋工具方法的參數型別描述項。 這兩個型別描述項會出現在**關聯編輯器**。 若要建立外部索引鍵關聯性，之間`Contact`實體和`SalesOrder`實體中，選擇`ContactID`每個欄位旁邊的識別項。  
  
 傳回目的地實體的集合之來源實體的關聯的導覽器方法中加入程式碼。 下列範例會傳回銷售訂單的連絡人。  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 傳回來源實體之目的地實體的關聯的導覽器方法中加入程式碼。 下列範例會傳回與銷售訂單相關的連絡人。  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>外部無索引鍵的關聯
 您可以建立關聯，而不需要將識別碼對應到欄位型別描述元。 來源實體沒有與目的地實體的直接關聯性時，請建立此類型的關聯。 例如，`SalesOrderDetail`資料表沒有主索引鍵中對應的外部索引鍵`Contact`資料表。  
  
 如果您想要顯示資訊`SalesOrderDetail`與相關的資料表`Contact`，您可以建立外部索引之間無索引鍵關聯`Contact`實體和`SalesOrderDetail`實體。  
  
 中的關聯巡覽方法`Contact`實體，傳回`SalesOrderDetail`實體聯結資料表，或藉由呼叫預存程序。  
  
 下列範例會傳回聯結資料表的所有銷售訂單詳細資料。  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 中的關聯巡覽方法`SalesOrderDetail`實體傳回相關`Contact`。 下列範例為其示範。  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>另請參閱
 [設計商務資料連接模型](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [如何： 建立實體之間的關聯](../sharepoint/how-to-create-an-association-between-entities.md)  
  
 
