---
title: "逐步解說： 下載 ClickOnce 部署 API 的要求組件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: f84d1cfa2208dc8a8b9d279a46ecf52676c0ae62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api"></a>逐步解說：依 ClickOnce 部署 API 的要求下載組件
根據預設，所有組件包含在[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]第一次執行應用程式時，會下載應用程式。 不過，您可能必須部分應用程式所使用的一小群使用者。 在此情況下，只有在建立組件的其中一種類型時，才會想要下載組件。 下列逐步解說將示範如何將標示為 「 選用 」 的應用程式中的某些組件，以及如何下載使用中的類別<xref:System.Deployment.Application>當 common language runtime (CLR) 要求其命名空間。  
  
> [!NOTE]
>  您的應用程式必須以完全信任執行，才能使用此程序。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說的其中一個：  
  
-   Windows SDK。 可以從 Microsoft 下載中心下載 Windows SDK。  
  
-   Visual Studio。  
  
## <a name="creating-the-projects"></a>建立專案  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>若要建立使用隨組件的專案  
  
1.  建立名為 ClickOnceOnDemand 的目錄。  
  
2.  開啟 Windows SDK 命令提示字元或[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]命令提示字元。  
  
3.  切換至 ClickOnceOnDemand 目錄。  
  
4.  產生公開/私密金鑰的金鑰組，使用下列命令：  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  使用 [記事本] 或其他文字編輯器，定義類別，名為`DynamicClass`具有單一內容，名為`Message`。  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  將文字儲存檔案名稱為`ClickOnceLibrary.cs`或`ClickOnceLibrary.vb`，視您使用 ClickOnceOnDemand 目錄的語言。  
  
7.  將檔案編譯成組件。  
  
    ```csharp  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  若要取得的公開金鑰語彙基元的組件，請使用下列命令：  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. 建立新的檔案，使用文字編輯器，並輸入下列程式碼。 此程式碼會建立 Windows Forms 應用程式，可在需要時下載 ClickOnceLibrary 組件。  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. 在程式碼中，找出呼叫<xref:System.Reflection.Assembly.LoadFile%2A>。  
  
11. 設定`PublicKeyToken`您先前擷取的值。  
  
12. 將檔案儲存為`Form1.cs`或`Form1.vb`。  
  
13. 編譯成可執行檔，使用下列命令。  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="marking-assemblies-as-optional"></a>將組件標示為選擇性  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>若要使用 MageUI.exe 標記為選擇性 ClickOnce 應用程式中的組件  
  
1.  使用 MageUI.exe 中，建立應用程式資訊清單中所述[逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 應用程式資訊清單，請使用下列設定：  
  
    -   命名應用程式資訊清單`ClickOnceOnDemand`。  
  
    -   上**檔案**頁面 ClickOnceLibrary.dll 列中，設定**檔案類型**欄**無**。  
  
    -   在**檔案**ClickOnceLibrary.dll 列中，類型 頁面上，`ClickOnceLibrary.dll`中**群組**資料行。  
  
2.  使用 MageUI.exe 中，建立部署資訊清單中所述[逐步解說： 手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。 部署資訊清單，請使用下列設定：  
  
    -   部署資訊清單的名稱`ClickOnceOnDemand`。  
  
## <a name="testing-the-new-assembly"></a>測試新的組件  
  
#### <a name="to-test-your-on-demand-assembly"></a>測試隨選組件  
  
1.  上傳您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Web 伺服器部署。  
  
2.  啟動應用程式部署與[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]從 Web 瀏覽器輸入 URL 的部署資訊清單。 如果您呼叫您[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]應用程式`ClickOnceOnDemand`，而且您將它上傳至 adatum.com 的根目錄，您的 URL 會看起來像這樣：  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  您的主要表單出現時，請按 <xref:System.Windows.Forms.Button>。 您應該會看到的訊息方塊視窗中，會讀取"Hello World ！"的字串。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Deployment.Application.ApplicationDeployment>