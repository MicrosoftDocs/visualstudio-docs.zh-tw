---
title: 如何-發行已啟用視覺樣式的 WPF 應用程式 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21c94cc7ab97070b138cbae108c617094faf09b5
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382207"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>如何：發佈已啟用視覺樣式的 WPF 應用程式

視覺化樣式讓通用控制項的外觀能夠根據使用者選擇的主題來變更。 根據預設，不會針對 Windows Presentation Foundation （WPF）應用程式啟用視覺化樣式，因此您必須手動加以啟用。 不過，為 WPF 應用程式啟用視覺化樣式，然後發佈方案，會導致錯誤。 本主題描述如何解決此錯誤，以及發行已啟用視覺化樣式的 WPF 應用程式的流程。 如需視覺化樣式的詳細資訊，請參閱[視覺化樣式總覽](/windows/desktop/Controls/visual-styles-overview)。 如需錯誤訊息的詳細資訊，請參閱針對[ClickOnce 部署中的特定錯誤進行疑難排解](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)。

 若要解決錯誤併發布解決方案，您必須執行下列工作：

- [在未啟用視覺化樣式的情況下發布解決方案](#publish-the-solution-without-visual-styles-enabled)。

- [建立資訊清單](#create-a-manifest-file)檔。

- 將[資訊清單檔案內嵌至已發行之方案的可執行檔中](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution)。

- [簽署應用程式和部署資訊清單](#sign-the-application-and-deployment-manifests)。

  然後，您可以將已發佈的檔案移至您想要讓使用者安裝應用程式的位置。

## <a name="publish-the-solution-without-visual-styles-enabled"></a>在未啟用視覺化樣式的情況下發布方案

1. 請確定您的專案未啟用視覺化樣式。 首先，檢查項目的資訊清單檔中是否有下列 XML。 然後，如果 XML 存在，請使用註解標記來括住 XML。

     根據預設，不會啟用視覺化樣式。

    ```xml
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```

     下列程式示範如何開啟與專案相關聯的資訊清單檔案。

    **若要在 Visual Basic 專案中開啟資訊清單檔**

    1. 在功能表列上，選擇 [專案]、[**專案***名稱*] [**屬性**]，其中*專案*名稱是您的 WPF 專案名稱。

         WPF 專案的屬性頁隨即出現。

    2. 在 [**應用程式**] 索引標籤上，選擇 [**查看 Windows 設定**]。

         隨即在程式**代碼編輯器**中開啟 app.config 檔案。

    **若要在 c # 專案中開啟資訊清單檔**

    1. 在功能表列上，選擇 [專案]、[**專案***名稱*] [**屬性**]，其中*專案*名稱是您的 WPF 專案名稱。

         WPF 專案的屬性頁隨即出現。

    2. 在 [**應用程式**] 索引標籤上，記下出現在 [資訊清單] 欄位中的名稱。 這是與您的專案相關聯的資訊清單名稱。

        > [!NOTE]
        > 如果**使用預設設定內嵌資訊清單**，或在資訊清單欄位中出現 [**建立沒有資訊清單的應用程式**]，則不會啟用視覺化樣式。 如果資訊清單檔案的名稱出現在 [資訊清單] 欄位中，請繼續進行此程式中的下一個步驟。

    3. 在 [方案總管]**** 中選擇 [顯示所有檔案]****。

         此按鈕會顯示所有專案專案，包括已排除的專案，以及通常隱藏的專案。 資訊清單檔會顯示為專案專案。

2. 建立併發布您的解決方案。 如需如何發佈方案的詳細資訊，請參閱[如何：使用發行嚮導發行 ClickOnce 應用程式](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。

## <a name="create-a-manifest-file"></a>建立資訊清單檔

1. 將下列 XML 貼入 [記事本] 檔案。

     此 XML 會描述包含支援視覺化樣式之控制項的元件。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <asmv1:assembly manifestVersion="1.0"
        xmlns="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
        xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
        <dependency>
            <dependentAssembly>
                <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
            </dependentAssembly>
        </dependency>
    </asmv1:assembly>
    ```

2. 在 [記事本] 中 **，按一下 [** 檔案]，然後按一下 [**另存**新檔]。

3. 在 [**另存**新檔] 對話方塊的 [**存檔類型**] 下拉式清單中，選取 [**所有**檔案]。

4. 在 [**檔案名**] 方塊中，將檔案命名為，並在檔案名結尾附加 *. manifest* 。 例如：*主題. 資訊清單*。

5. 選擇 [**流覽資料夾]** 按鈕，選取任何資料夾，然後按一下 [**儲存**]。

    > [!NOTE]
    > 其餘的程式假設此檔案的名稱為*themes* ，而且檔案會儲存至電腦上的*C：\temp*目錄。

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>將資訊清單檔案內嵌至已發行之方案的可執行檔

1. 開啟**Visual Studio 命令提示**字元。

    如需如何開啟**Visual Studio 命令提示**字元的詳細資訊，請參閱[命令提示](/dotnet/framework/tools/developer-command-prompt-for-vs)字元。

   > [!NOTE]
   > 其餘步驟會針對您的解決方案進行下列假設：
   >
   > - 解決方案的名稱是**MyWPFProject**。
   > - 此解決方案位於下列目錄： `%UserProfile%\Documents\Visual Studio 2010\Projects\` 。
   >
   > - 解決方案會發佈到下列目錄： `%UserProfile%\Documents\Visual Studio 2010\Projects\publish` 。
   > - 已發行應用程式檔的最新版本位於下列目錄：`%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > 您不需要使用前述的名稱或目錄位置。 以上所述的名稱和位置僅用於說明發佈解決方案所需的步驟。

2. 在命令提示字元中，將路徑變更為包含已發行應用程式檔最新版本的目錄。 下列範例示範此步驟。

   ```cmd
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. 在命令提示字元中，執行下列命令，以將資訊清單檔案內嵌至應用程式的可執行檔。

   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a>簽署應用程式和部署資訊清單

1. 在命令提示字元中，執行下列命令，以從目前目錄中的可執行檔移除 .deploy 延伸模組 *。*

   ```cmd
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > 這個範例假設只有一個檔案具有 *.deploy*副檔名。 請確定您重新命名此目錄中副檔名為 *.deploy*的所有檔案。

2. 在命令提示字元中，執行下列命令來簽署應用程式資訊清單。

   ```cmd
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > 這個範例假設您使用專案的 *.pfx*檔案來簽署資訊清單。 如果您不是簽署資訊清單，可以省略 `-cf` 此範例中使用的參數。 如果您要使用需要密碼的憑證來簽署資訊清單，請指定 `-password` 選項（ `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` ）。

3. 在命令提示字元中，執行下列命令，將 .deploy 副檔名新增至您在此程式的上一個步驟中重新命名的檔案名 *。*

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > 這個範例假設只有一個檔案具有 *.deploy*副檔名。 請確定您重新命名此目錄中的所有檔案，這些檔案先前具有 *. deploy*副檔名。

4. 在命令提示字元中，執行下列命令來簽署部署資訊清單。

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > 這個範例假設您使用專案的 *.pfx*檔案來簽署資訊清單。 如果您不是簽署資訊清單，可以省略 `-cf` 此範例中使用的參數。 如果您要使用需要密碼的憑證來簽署資訊清單，請指定 `-password` 選項，如下列範例所示： `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` 。

   執行這些步驟之後，您可以將已發佈的檔案移至您想要讓使用者安裝應用程式的位置。 如果您想要經常更新解決方案，可以將這些命令移入腳本中，並在每次發行新版本時執行腳本。

## <a name="see-also"></a>另請參閱

-[針對 ClickOnce 部署中的特定錯誤進行疑難排解](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [視覺化樣式總覽](/windows/desktop/Controls/visual-styles-overview)
- [啟用視覺化樣式](/windows/desktop/Controls/cookbook-overview)
- [命令提示字元](/dotnet/framework/tools/developer-command-prompt-for-vs)
