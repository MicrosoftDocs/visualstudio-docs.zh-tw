---
title: 使用 (ClickOnce API) 的設計工具視需要下載元件
description: 瞭解如何使用設計工具將 ClickOnce 應用程式中的特定元件標示為選擇性，並在 common language runtime 需要時加以下載。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7bb30b26e859708d295a31bd45b310897e4bcaac
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216991"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>逐步解說：使用設計工具以 ClickOnce 部署 API 依需求下載元件
第一次執行 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式時，預設會下載應用程式中包含的所有組件。 不過，可能是小部分使用者所使用之應用程式的組件。 在此情況下，只有在建立組件的其中一種類型時，才會想要下載組件。 下列逐步解說示範如何將應用程式中的特定組件標示為「選擇性」，以及在 Common Language Runtime 需要時，使用 <xref:System.Deployment.Application> 中的類別來如何下載它們。

> [!NOTE]
> 您的應用程式必須以完全信任執行，才能使用此程序。

> [!NOTE]
> 您看到的對話方塊與功能表命令，可能會因您所使用的設定或版本，而與說明中所述不同。 若要變更設定，請在 [工具]  功能表上按一下 [匯入和匯出設定]  。 如需詳細資訊，請參閱[重設設定](../ide/environment-settings.md#reset-settings)。

## <a name="create-the-projects"></a>建立專案

### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>使用 Visual Studio 建立使用隨選組件的專案

1. 在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]中建立新的 Windows Forms 專案。 在 [檔案] 功能表上，指向 [加入]，然後按一下 [新增專案]。 選擇對話方塊中的 [類別庫]  專案，並將它命名為 `ClickOnceLibrary`。

   > [!NOTE]
   > 在 Visual Basic 中，建議您修改專案屬性，以將此專案的根命名空間變更為 `Microsoft.Samples.ClickOnceOnDemand` 或您選擇的命名空間。 為求簡單起見，本逐步解說中的兩個專案都位於相同的命名空間中。

2. 定義具有單一屬性 `DynamicClass` 的 `Message`類別。

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs" id="Snippet1":::

3. 在方案總管 中，選取 Windows Forms 專案。 將參考新增至 <xref:System.Deployment.Application> 組件，並將專案參考新增至 `ClickOnceLibrary` 專案。

   > [!NOTE]
   > 在 Visual Basic 中，建議您修改專案屬性，以將此專案的根命名空間變更為 `Microsoft.Samples.ClickOnceOnDemand` 或您選擇的命名空間。 為求簡單起見，本逐步解說中的兩個專案都位於相同的命名空間中。

4. 以滑鼠右鍵按一下表單，並從功能表中按一下 [檢視程式碼]  ，然後在表單中新增下列參考。

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet1":::

5. 新增下列程式碼，以視需要下載此組件。 此程式碼示範如何使用泛型 <xref:System.Collections.DictionaryBase.Dictionary%2A> 類別將一組組件對應至群組名稱。 因為我們只會下載本逐步解說中的單一組件，所以我們的群組中只會有一個組件。 在實際的應用程式中，您可能會想要同時下載與應用程式中單一功能相關的所有組件。 對應資料表可讓您輕鬆地進行這項作業，方法是將屬於某個功能的所有 DLL 都與下載群組名稱產生關聯。

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet2":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet2":::

6. 在 [檢視] 功能表上，按一下 [工具箱]。 將 <xref:System.Windows.Forms.Button> 從 [工具箱]  拖曳至表單。 按兩下按鈕，並將下列程式碼新增至 <xref:System.Windows.Forms.Control.Click> 事件處理常式。

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet3":::

## <a name="mark-assemblies-as-optional"></a>將元件標示為選擇性

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>使用 Visual Studio 將組件標示為 ClickOnce 應用程式中的選用項目

1. 以滑鼠右鍵按一下方案總管  中的 Windows Forms 專案，然後按一下 [屬性] 。 選取 [發行]  索引標籤。

2. 按一下 [應用程式檔案]  按鈕。

3. 尋找 *ClickOnceLibrary.dll* 的清單。 將 [發行狀態]  下拉式方塊設定成 [包含] 。

4. 展開 [群組]  下拉式方塊，然後選取 [新增] 。 輸入名稱 `ClickOnceLibrary` 作為新的群組名稱。

5. 繼續發佈您的應用程式，如 [如何：使用發佈嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)中所述。

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>使用資訊清單產生和編輯工具 (圖形化用戶端 (MageUI.exe)) 將組件標示為 ClickOnce 應用程式中的選用項目

1. 依照 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)中所述，建立您的資訊清單。

2. 關閉 MageUI.exe 之前，請選取包含您部署之應用程式資訊清單的索引標籤，然後在該索引標籤內選取 [檔案]  索引標籤。

3. 在應用程式檔案清單中尋找 ClickOnceLibrary.dll，並將其 [檔案類型]  資料行設定成 [無] 。 在 [群組]  資料行中，輸入 `ClickOnceLibrary.dll`。

## <a name="test-the-new-assembly"></a>測試新的元件

測試隨選組件：

1. 啟動使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]所部署的應用程式。

2. 您的主要表單出現時，請按 <xref:System.Windows.Forms.Button>。 您應該會在訊息方塊視窗中看到 "Hello, World!" 字串。

## <a name="see-also"></a>另請參閱

- <xref:System.Deployment.Application.ApplicationDeployment>
