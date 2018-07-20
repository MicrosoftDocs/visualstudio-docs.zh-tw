---
title: 逐步解說： 下載附屬組件，依需求以 ClickOnce 部署 API 使用設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows Forms, globalization
- ClickOnce deployment, globalization
- localization, Windows Forms
- ClickOnce, on-demand download
- Windows Forms, localization
- ClickOnce deployment, localization
- walkthroughs, localization
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 79c5616a9233466c71ca036c4c0cb70d43649979
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154855"
---
# <a name="walkthrough-download-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>逐步解說： 下載附屬組件，依需求以 ClickOnce 部署 API 使用設計工具
透過使用附屬組件，Windows Forms 應用程式可以設定為適用多個文化特性。 *「附屬組件」* (Satellite Assembly) 為包含文化特性 (除了應用程式的預設文化特性以外) 之應用程式資源的組件。  
  
 中所述[當地語系化 ClickOnce 應用程式](../deployment/localizing-clickonce-applications.md)，您可以包含在相同的多個文化特性的多個附屬組件[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]部署。 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 預設會下載您部署中所有的附屬組件到用戶端電腦，儘管單一用戶可能只需要一個附屬組件。  
  
 本逐步解說示範如何標示您的附屬組件為選擇性，並僅下載用戶端電腦目前文化特性所需要的附屬組件。  
  
> [!NOTE]
>  為了測試用途，下列程式碼範例以程式設計的方式設定文化特性為 `ja-JP`。 如需為生產環境調整程式碼的相關資訊，請參閱本主題＜後續步驟＞一節。  
  
### <a name="to-mark-satellite-assemblies-as-optional"></a>將附屬組件標示為選擇性  
  
1.  建置您的專案。 這個步驟將會針對您在進行當地語系化的所有文化特性產生附屬組件。  
  
2.  在 方案總管 中，您的專案名稱上按一下滑鼠右鍵，然後按一下 **屬性**。  
  
3.  按一下 **發佈**索引標籤，然後再按一下**應用程式檔案**。  
  
4.  選取 **顯示所有檔案**核取方塊，顯示附屬組件。 所有附屬組件預設都會包含在部署中，而且會顯示在這個對話方塊中。  
  
     附屬組件都會有名稱形式 *\<isoCode > \ApplicationName.resources.dll*，其中\<isoCode > 是 RFC 1766 格式的語言識別項。  
  
5.  按一下 **的新**中**下載群組**為每個語言識別碼的清單。 在系統提示您輸入下載群組名稱時，請輸入語言識別項。 比方說，是日文的附屬組件中，您會指定將下載群組名稱`ja-JP`。  
  
6.  關閉**應用程式檔案** 對話方塊。  
  
### <a name="to-download-satellite-assemblies-on-demand-in-c"></a>在 C# 內視需要下載附屬組件 
  
1.  開啟 *Program.cs* 檔案。 如果看不到此檔案在方案總管 中，選取您的專案，並在**專案**功能表上，按一下**顯示所有檔案**。  
  
2.  使用下列程式碼來下載適當的附屬組件，並啟動您的應用程式。  
  
     [!code-csharp[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
### <a name="to-download-satellite-assemblies-on-demand-in-visual-basic"></a>在 Visual Basic 內視需要下載附屬組件  
  
1.  在 **屬性**視窗中的應用程式中，按一下 **應用程式** 索引標籤。  
  
2.  在頁面底部的索引標籤上，按一下**檢視應用程式事件**。  
  
3.  開頭加入下列 imports *ApplicationEvents.VB*檔案。  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
4.  將下列程式碼加入 `MyApplication` 類別。  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
## <a name="next-steps"></a>後續步驟  
 在生產環境中，您可能需要移除程式碼範例中將 <xref:System.Threading.Thread.CurrentUICulture%2A> 設定為特定值的那一行，因為用戶端電腦預設會設定正確的值。 當您的應用程式在日文的用戶端電腦上執行時， <xref:System.Threading.Thread.CurrentUICulture%2A> 預設會是 `ja-JP` 。 在部署應用程式前，以程式設計方式設定這個值是測試附屬組件的一個好方法。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 下載附屬組件，依需求以 ClickOnce 部署 API](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [當地語系化 ClickOnce 應用程式](../deployment/localizing-clickonce-applications.md)
