---
title: 如何： 發行已啟用視覺化樣式的 WPF 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af0a07abe1cbb380acde91067e3e6252d0cd8596
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830050"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>如何： 發行已啟用視覺化樣式的 WPF 應用程式
視覺化樣式會啟用常見的控制項，以根據使用者選擇的佈景主題變更的外觀。 根據預設，已啟用視覺化樣式未針對 Windows Presentation Foundation (WPF) 應用程式，因此您必須手動啟用它們。 不過，啟用視覺化樣式的 WPF 應用程式，然後發佈方案會導致錯誤。 本主題說明如何解決此錯誤，發佈已啟用視覺化樣式的 WPF 應用程式的程序。 如需視覺化樣式的詳細資訊，請參閱[視覺化樣式概觀](/windows/desktop/Controls/visual-styles-overview)。 如需詳細的錯誤訊息的詳細資訊，請參閱[疑難排解 ClickOnce 部署的特定錯誤](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)。  
  
 若要解決此錯誤，並發行方案，您必須執行下列工作：  
  
- [發行方案，而不需要啟用視覺化樣式](#publish-the-solution-without-visual-styles-enabled)。  
  
- [建立資訊清單檔](#create-a-manifest-file)。  
  
- [發佈方案的可執行檔中嵌入資訊清單檔](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution)。  
  
- [簽署應用程式和部署資訊清單](#sign-the-application-and-deployment-manifests)。  
  
  然後，您可以將已發行的檔案移至 您從中安裝應用程式的終端使用者的位置。  
  
##  <a name="publish-the-solution-without-visual-styles-enabled"></a>發行方案，而不需要啟用視覺化樣式  
  
1.  請確定您的專案沒有啟用視覺化樣式。 首先，檢查您的專案資訊清單檔案，如下列 XML 程式碼。 然後，如果 XML 存在時，括住的 XML 註解標記。  
  
     根據預設，不會啟用視覺化樣式。  
  
    ```xml  
    <dependency>    <dependentAssembly>      <assemblyIdentity          type="win32"          name="Microsoft.Windows.Common-Controls"          version="6.0.0.0"          processorArchitecture="*"          publicKeyToken="6595b64144ccf1df"          language="*"        />    </dependentAssembly>  </dependency>  
    ```  
  
     下列程序示範如何開啟與您的專案相關聯的資訊清單檔案。  
  
    ###### <a name="to-open-the-manifest-file-in-a-visual-basic-project"></a>若要開啟 Visual Basic 專案中的 資訊清單檔案  
  
    1.  在功能表列上選擇 **專案**， *ProjectName* **屬性**，其中*ProjectName*是 WPF 專案的名稱。  
  
         您的 WPF 專案的屬性頁會出現。  
  
    2.  在 **應用程式**索引標籤上，選擇**檢視 Windows 設定**。  
  
         在中開啟 app.manifest 檔案**程式碼編輯器**。  
  
    ###### <a name="to-open-the-manifest-file-in-a-c-project"></a>若要開啟 C# 專案中的 資訊清單檔案  
  
    1.  在功能表列上選擇 **專案**， *ProjectName* **屬性**，其中*ProjectName*是 WPF 專案的名稱。  
  
         您的 WPF 專案的屬性頁會出現。  
  
    2.  在 **應用程式**索引標籤上，記下資訊清單的欄位中出現的名稱。 這是與您專案相關聯的資訊清單名稱。  
  
        > [!NOTE]
        >  如果**使用預設設定嵌入資訊清單**或是**Vytvořit aplikaci bez 資訊清單**會出現在資訊清單的欄位中，不會啟用視覺化樣式。 如果資訊清單檔案的名稱會出現在資訊清單的欄位，請繼續此程序的下一個步驟。  
  
    3.  在 **方案總管**，選擇**顯示所有檔案**。  
  
         此按鈕會顯示所有的專案項目，包括已排除以及一些通常會隱藏。 資訊清單檔會顯示為專案項目。  
  
2.  建置及發佈您的解決方案。 如需如何發佈方案的詳細資訊，請參閱[如何： 發行 ClickOnce 應用程式使用發行精靈](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)。  
  
## <a name="create-a-manifest-file"></a>建立資訊清單檔  
  
1.  將下列 XML 程式碼貼到 [記事本] 檔案。  
  
     這段 XML 會說明包含支援視覺化樣式的控制項的組件。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?><asmv1:assembly manifestVersion="1.0"                xmlns="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"                xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  <dependency>    <dependentAssembly>      <assemblyIdentity        type="win32"        name="Microsoft.Windows.Common-Controls"        version="6.0.0.0"        processorArchitecture="*"        publicKeyToken="6595b64144ccf1df"        language="*"        />    </dependentAssembly>  </dependency></asmv1:assembly>  
    ```  
  
2.  在記事本中，按一下**檔案**，然後按一下**另存新檔**。  
  
3.  在 **另存新檔**對話方塊中，於**存檔類型**下拉式清單中，選取**所有檔案**。  
  
4.  在 **檔案名稱**，將檔案命名並附加 *.manifest*檔案名稱的結尾。 例如： *themes.manifest*。  
  
5.  選擇**瀏覽資料夾**按鈕，選取任何資料夾，然後按一下 **儲存**。  
  
    > [!NOTE]
    >  其餘的程序假設這個檔案的名稱是*themes.manifest* ，將檔案儲存到*C:\temp*目錄在您的電腦上。  
  
## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>發佈方案的可執行檔中嵌入資訊清單檔案  
  
1. 開啟**Visual Studio 命令提示字元**。  
  
    如需有關如何開啟**Visual Studio 命令提示字元**，請參閱[命令提示字元](/dotnet/framework/tools/developer-command-prompt-for-vs)。  
  
   > [!NOTE]
   >  其餘的步驟進行下列假設有關您的解決方案：  
   > 
   > - 方案的名稱是**MyWPFProject**。  
   >   -   方案位於下列目錄： `%UserProfile%\Documents\Visual Studio 2010\Projects\`。  
   > 
   >   將解決方案發佈到下列目錄： `%UserProfile%\Documents\Visual Studio 2010\Projects\publish`。  
   >   -   最新版的已發行的應用程式檔案位於下列目錄： `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`  
   > 
   >   您沒有使用上述的目錄位置或名稱。 上面所述的位置與名稱是只能用來說明發佈您的解決方案所需的步驟。  
  
2. 在命令提示字元中，將路徑變更為包含最新版的已發行的應用程式檔案的目錄。 下列範例示範此步驟。  
  
   ```cmd  
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"  
   ```  
  
3. 在命令提示字元中，執行下列命令，以將資訊清單檔內嵌到應用程式的可執行檔。  
  
   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy  
   ```  
  
## <a name="sign-the-application-and-deployment-manifests"></a>簽署應用程式和部署資訊清單  
  
1. 在命令提示字元中，執行下列命令來移除 *.deploy*從目前目錄中可執行檔。  
  
   ```cmd  
   ren MyWPFApp.exe.deploy MyWPFApp.exe  
   ```  
  
   > [!NOTE]
   >  這個範例假設只有一個檔案 *.deploy*副檔名。 請確定您已重新命名此目錄中的所有檔案具有 *.deploy*副檔名。  
  
2. 在命令提示字元中，執行下列命令來簽署應用程式資訊清單。  
  
   ```cmd  
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  這個範例假設您使用簽署資訊清單 *.pfx*專案檔案。 如果您不會簽署資訊清單，您可以省略`-cf`此範例中使用的參數。 如果您所簽署的憑證需要密碼的資訊清單，指定`-password`選項 (`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`)。  
  
3. 在命令提示字元中，執行下列命令，以新增 *.deploy*您此程序的上一個步驟中重新命名的檔案名稱的擴充功能。  
  
   ```  
   ren MyWPFApp.exe MyWPFApp.exe.deploy  
   ```  
  
   > [!NOTE]
   >  這個範例假設只有一個檔案已 *.deploy*副檔名。 請確定您已重新命名這個先前的目錄中的所有檔案 *.deploy*副檔名。  
  
4. 在命令提示字元中，執行下列命令來簽署部署資訊清單。  
  
   ```  
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx  
   ```  
  
   > [!NOTE]
   >  這個範例假設您使用簽署資訊清單 *.pfx*專案檔案。 如果您不會簽署資訊清單，您可以省略`-cf`此範例中使用的參數。 如果您所簽署的憑證需要密碼的資訊清單，指定`-password`選項，如此範例所示：`For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password`。  
  
   在您執行這些步驟之後，您可以移動已發行的檔案到您從中安裝應用程式的終端使用者的位置。 如果您想要經常更新方案，您可以將這些命令移至 指令碼，並執行指令碼每次您發行新版本。  
  
## <a name="see-also"></a>另請參閱

-[疑難排解 ClickOnce 部署中的特定錯誤](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [視覺化樣式的概觀](/windows/desktop/Controls/visual-styles-overview)
- [啟用視覺化樣式](/windows/desktop/Controls/cookbook-overview)
- [命令提示字元](/dotnet/framework/tools/developer-command-prompt-for-vs)
