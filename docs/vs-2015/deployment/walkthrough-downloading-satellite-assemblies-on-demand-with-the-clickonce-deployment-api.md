---
title: 逐步解說：使用 ClickOnce 部署 API 依需求下載附屬元件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a84de037661992d1ee185bea2a70db74dac5e618
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686345"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>逐步解說：依 ClickOnce 部署 API 的要求下載附屬組件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

透過使用附屬組件，Windows Forms 應用程式可以設定為適用多個文化特性。 *「附屬組件」* (Satellite Assembly) 為包含文化特性 (除了應用程式的預設文化特性以外) 之應用程式資源的組件。  
  
 如同在 [當地語系化 ClickOnce 應用程式](../deployment/localizing-clickonce-applications.md)中所討論，您可以在相同部署中包含多個不同文化特性的附屬元件 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 。 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 預設會下載您部署中所有的附屬組件到用戶端電腦，儘管單一用戶可能只需要一個附屬組件。  
  
 本逐步解說示範如何標示您的附屬組件為選擇性，並僅下載用戶端電腦目前文化特性所需要的附屬組件。 下列程序使用的工具可在 [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]取得。 您也可以在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]執行這個工作。  另請參閱 [逐步解說：使用設計工具依 ClickOnce 部署 API 的要求下載附屬組件](https://msdn.microsoft.com/library/ms366788\(v=vs.110\)) 或 [逐步解說：使用設計工具依 ClickOnce 部署 API 的要求下載附屬組件](https://msdn.microsoft.com/library/ms366788\(v=vs.120\))。  
  
> [!NOTE]
> 為了測試用途，下列程式碼範例以程式設計的方式設定文化特性為 `ja-JP`。 如需為生產環境調整程式碼的相關資訊，請參閱本主題＜後續步驟＞一節。  
  
## <a name="prerequisites"></a>Prerequisites  
 本主題假設您知道如何使用 Visual Studio 將當地語系化的資源新增至您的應用程式。 如需詳細指示，請參閱 [逐步解說：當地語系化 Windows Forms](https://msdn.microsoft.com/library/vstudio/y99d1cd3\(v=vs.100\).aspx)。  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>隨需下載附屬組件  
  
1. 將下列程式碼加入您的應用程式，以便能夠隨需下載附屬組件。  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs#1)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb#1)]  
  
2. 使用 [Resgen.exe (資源檔 ](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) 產生器) 或，為您的應用程式產生附屬元件 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。  
  
3. 使用 MageUI.exe 產生應用程式資訊清單，或開啟現有的應用程式資訊清單。 如需有關這項工具的詳細資訊，請參閱 < [MageUI.exe (圖形用戶端、資訊清單產生和編輯工具)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)。  
  
4. 按一下 [檔案] **** 索引標籤。  
  
5. 按一下 **省略號** 按鈕 (**...**) 並選取包含您所有應用程式元件和檔案的目錄，包括您使用 Resgen.exe 產生的附屬元件。  (附屬元件的名稱格式會是 *isoCode*\ApplicationName.resources.dll，其中 *isoCode* 是 RFC 1766 格式的語言識別項。 )   
  
6. 按一下 [填入] **** 將檔案加入您的部署。  
  
7. 選取每個附屬組件的 [選擇性] **** 核取方塊。  
  
8. 設定群組欄位到每個附屬組件的 ISO 語言識別項。 以日文的附屬組件為例，您會將下載群組名稱指定為 `ja-JP`取得。 這可讓您在步驟 1 加入的程式碼，根據使用者之 <xref:System.Threading.Thread.CurrentUICulture%2A> 屬性設定，下載適合的附屬組件。  
  
## <a name="next-steps"></a>後續步驟  
 在生產環境中，因為用戶端電腦上會有正確的預設值，所以您可能需要移除行程式碼範例中，將 <xref:System.Threading.Thread.CurrentUICulture%2A> 設定為特定值的行。 當您的應用程式在日文的用戶端電腦上執行時， <xref:System.Threading.Thread.CurrentUICulture%2A> 預設會是 `ja-JP` 。 在部署您的應用程式之前，以程式設計方式設定這個值以測試附屬組件，是個好方法。  
  
## <a name="see-also"></a>另請參閱  
 [當地語系化 ClickOnce 應用程式](../deployment/localizing-clickonce-applications.md)
