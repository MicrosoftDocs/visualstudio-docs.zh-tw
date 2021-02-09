---
title: '視需要下載元件 (ClickOnce API) '
description: 瞭解如何將 ClickOnce 應用程式中的特定元件標示為選擇性，並在 common language runtime 需要時加以下載。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a87bcd8b51bc393921d21d838943d5e1fe8f02a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917340"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>逐步解說：使用 ClickOnce 部署 API 依需求下載元件
根據預設，應用程式中包含的所有元件 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 都會在第一次執行應用程式時下載。 不過，您的應用程式中可能會有一小部分使用者使用的部分。 在此情況下，只有在建立組件的其中一種類型時，才會想要下載組件。 下列逐步解說示範如何將應用程式中的特定組件標示為「選擇性」，以及在 Common Language Runtime 需要時，使用 <xref:System.Deployment.Application> 命名空間中的類別來下載它們。

> [!NOTE]
> 您的應用程式必須以完全信任執行，才能使用此程序。

## <a name="prerequisites"></a>必要條件
 您將需要下列其中一個元件，才能完成此逐步解說：

- Windows SDK。 您可以從 Microsoft 下載中心下載 Windows SDK。

- Visual Studio。

## <a name="create-the-projects"></a>建立專案

#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>若要建立使用隨選元件的專案

1. 建立名為 ClickOnceOnDemand 的目錄。

2. 開啟 Windows SDK 命令提示字元或 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 命令提示字元。

3. 變更至 ClickOnceOnDemand 目錄。

4. 使用下列命令來產生公開/私密金鑰組：

   ```cmd
   sn -k TestKey.snk
   ```

5. 使用 [記事本] 或其他文字編輯器，定義名為的類別， `DynamicClass` 並使用名為的單一屬性 `Message` 。

    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]

6. 將文字儲存為名為 *ClickOnceLibrary.cs* 或 *clickoncelibrary.dll* 的檔案（視您使用的語言而定）至 *ClickOnceOnDemand* 目錄。

7. 將檔案編譯成元件。

   ```csharp
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs
   ```

   ```vb
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb
   ```

8. 若要取得元件的公開金鑰 token，請使用下列命令：

   ```cmd
   sn -T ClickOnceLibrary.dll
   ```

9. 使用文字編輯器建立新的檔案，並輸入下列程式碼。 此程式碼會建立 Windows Forms 應用程式，以在必要時下載 Clickoncelibrary.dll 元件。

     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]

10. 在程式碼中，找出的呼叫 <xref:System.Reflection.Assembly.LoadFile%2A> 。

11. 設定 `PublicKeyToken` 為您稍早取出的值。

12. 請將檔案儲存為 *Form1.cs* 或 *form1.vb。*

13. 使用下列命令將它編譯成可執行檔。

    ```csharp
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs
    ```

    ```vb
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb
    ```

## <a name="mark-assemblies-as-optional"></a>將元件標示為選擇性

#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>使用 MageUI.exe 將元件標示為 ClickOnce 應用程式中的選擇性

1. 使用 *MageUI.exe*，依照 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)中所述的方式建立應用程式資訊清單。 使用應用程式資訊清單的下列設定：

    - 命名應用程式資訊清單 `ClickOnceOnDemand` 。

    - 在 [檔案 **] 頁面的** [ *ClickOnceLibrary.dll* ] 資料列中，將 [ **檔案類型** ] 資料行設定為 [ **無**]。

    - 在 [檔案 **] 頁面的** [ *ClickOnceLibrary.dll* ] 資料列中，輸入 `ClickOnceLibrary.dll` [ **群組** ] 資料行。

2. 使用 *MageUI.exe*，依照 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)中所述的方式建立部署資訊清單。 針對部署資訊清單，請使用下列設定：

    - 命名部署資訊清單 `ClickOnceOnDemand` 。

## <a name="testing-the-new-assembly"></a>測試新的組件

#### <a name="to-test-your-on-demand-assembly"></a>測試隨選組件

1. 將您的部署上傳 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 至 Web 服務器。

2. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]輸入部署資訊清單的 URL，以啟動從網頁瀏覽器部署的應用程式。 如果您呼叫您的 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式 `ClickOnceOnDemand` ，並將它上傳至 adatum.com 的根目錄，您的 URL 看起來會像這樣：

   ```
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application
   ```

3. 您的主要表單出現時，請按 <xref:System.Windows.Forms.Button>。 您應該會在訊息方塊視窗中看見內容為 "Hello, World!" 的字串。

## <a name="see-also"></a>另請參閱
- <xref:System.Deployment.Application.ApplicationDeployment>