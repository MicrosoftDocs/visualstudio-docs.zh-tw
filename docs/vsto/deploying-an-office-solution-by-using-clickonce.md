---
title: 使用 ClickOnce 部署 Office 方案
description: 瞭解當您使用 ClickOnce 時，如何使用較少的步驟來部署 Office 方案。 如果您發行更新，方案會自動偵測並安裝更新。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 03b4f3d2f1a342f6c1977d616793634500850e7a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828614"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>使用 ClickOnce 部署 Office 方案
  使用 ClickOnce 只需要幾個步驟就能部署 Office 方案。 如果您發行更新，方案會自動偵測並安裝更新。 不過，ClickOnce 要求您針對電腦上的每個使用者分別安裝方案。 因此，如果有一位以上的使用者要在同一部電腦上執行您的方案，您應該考慮使用 Windows Installer (*.msi) 。*

## <a name="in-this-topic"></a>本主題內容

- [發行方案](#Publish)

- [決定您想要將信任授與方案的方式](#Trust)

- [協助使用者安裝方案](#Helping)

- [將方案的文件放置到使用者的電腦上 (僅適用於文件層級自訂)](#Put)

- [將方案的文件放置到執行 SharePoint 的伺服器上 (僅適用於文件層級自訂)](#SharePoint)

- [建立自訂安裝程式](#Custom)

- [發行更新](#Update)

- [變更方案的安裝位置](#Location)

- [將方案復原為舊版](#Roll)

  如需有關如何藉由建立 Windows Installer 檔案來部署 Office 方案的詳細資訊，請參閱 [使用 Windows Installer 部署 office 方案](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)。

## <a name="publish-the-solution"></a><a name="Publish"></a> 發佈方案
 您可以使用 [ **發佈嚮導]** 或 [ **專案設計** 工具] 發行您的方案。 在這個程式中，您將使用 [ **專案設計** 工具]，因為它會提供一組完整的發行選項。 請參閱 [Visual Studio&#41;中的發佈嚮導 &#40;Office 開發 ](../vsto/publish-wizard-office-development-in-visual-studio.md)。

#### <a name="to-publish-the-solution"></a>若要發行方案

1. 在 **方案總管** 中，選擇為您的專案命名的節點。

2. 在功能表列上，選擇 [專案]、[**專案***名稱*]**屬性**。

3. 在 [ **專案設計** 工具] 中，選擇 [ **發行** ] 索引標籤，如下圖所示。

    ![[專案設計工具] 中的 [發行] 索引標籤](../vsto/media/vsto-publishtab.png "[專案設計工具] 中的 [發行] 索引標籤")

4. 在 [ **發行資料夾位置 (ftp 伺服器或檔案路徑)** ] 方塊中，輸入您要 **專案設計** 工具複製方案檔的資料夾路徑。

    您可以輸入下列任何類型的路徑。

   - 本機路徑 (例如， *C:\FolderName\FolderName*) 。

   - 統一命名慣例 (UNC) 路徑到網路上的資料夾 (例如， *\\ \ServerName\FolderName*) 。

   - 相對路徑 (例如 *PublishFolder \\*，這是預設發佈專案) 的資料夾。

5. 在 [ **安裝資料夾 URL** ] 方塊中，輸入終端使用者可在其中找到您解決方案的位置完整路徑。

    如果您還不知道位置，請勿在此欄位中輸入任何欄位。 根據預設，ClickOnce 會在您的使用者安裝方案的資料夾中尋找更新。

6. 選擇 [ **必要條件** ] 按鈕。

7. 在 [ **必要條件** ] 對話方塊中，確定已選取 [ **建立安裝程式以安裝必要條件元件** ] 核取方塊。

8. 在 [ **選擇要安裝的必要條件** ] 清單中，選取 **Windows Installer 4.5** 和適當 .NET Framework 套件的核取方塊。

    例如，如果您的方案以為目標 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] ，請選取 [ **Windows Installer 4.5** ] 和 [ **Microsoft .NET Framework 4.5 Full**] 的核取方塊。

9. 如果您的方案以 .NET Framework 4.5 為目標，也請選取 [ **Visual Studio 2010 Tools For Office Runtime** ] 核取方塊。

    > [!NOTE]
    > 依預設，這個核取方塊不會出現。 若要顯示這個核取方塊，您必須建立啟動載入器套件。 請參閱 [使用 Visual Studio 2012 建立 Office 2013 VSTO 增益集](create-vsto-add-ins-for-office-by-using-visual-studio.md)的啟動載入器套件。

10. 在 [ **指定必要條件的安裝位置**] 下，選擇出現的其中一個選項，然後選擇 [ **確定]** 按鈕。

     下表會說明每個選項。

    |選項|Description|
    |------------|-----------------|
    |**從元件廠商的網站下載必要條件**|系統會提示使用者下載並安裝廠商提供的這些必要條件。|
    |**從應用程式的相同位置下載必要條件**|必要軟體會隨方案安裝。 如果您選擇這個選項，Visual Studio 會自動將所有必要條件套件複製到發行位置。 必要條件套件必須放在開發電腦上，這個選項才能正常運作。|
    |**從下列位置下載必要條件**|Visual Studio 會將所有必要條件套件複製到您指定的位置，並且隨方案安裝這些套件。|

     請參閱 [必要條件對話方塊](../ide/reference/prerequisites-dialog-box.md)。

11. 選擇 [ **更新** ] 按鈕，指定您希望每位使用者的 VSTO 增益集或自訂檢查更新的頻率，然後選擇 [ **確定]** 按鈕。

    > [!NOTE]
    > 如果您要使用 CD 或卸載式磁片磁碟機進行部署，請選擇 [ **永遠不檢查更新** ] 選項按鈕。

     如需有關如何發佈更新的詳細資訊，請參閱 [發佈更新](#Update)。

12. 選擇 [ **選項** ] 按鈕，檢查 [ **選項** ] 對話方塊中的選項，然後選擇 [ **確定]** 按鈕。

13. 選擇 [ **立即發佈** ] 按鈕。

     Visual Studio 會將下列資料夾和檔案加入至您在本程序前段指定的發行資料夾。

    - [ **應用程式檔** ] 資料夾。

    - 安裝程式。

    - 部署資訊清單，會指向最新版本的部署資訊清單。

      [ **應用程式檔** ] 資料夾包含您發佈之每個版本的子資料夾。 每個版本專屬子資料夾都包含下列檔案。

    - 應用程式資訊清單。

    - 部署資訊清單。

    - 自訂組件。

      下圖顯示 Outlook VSTO 增益集的發行資料夾結構。

      ![發行資料夾結構](../vsto/media/publishfolderstructure.png "發行資料夾結構")

    > [!NOTE]
    > ClickOnce 會將 *.deploy* 副檔名附加至元件，以便 Internet Information Services 的安全安裝 (IIS) 不會因為不安全的副檔名而封鎖這些檔案。 當使用者安裝方案時，ClickOnce 會移除 *.deploy* 副檔名。

14. 將方案檔複製到您在本程序前段指定的安裝位置。

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a> 決定您要如何將信任授與解決方案
 在使用者電腦上執行方案之前，您必須先授與信任，或是使用者必須在安裝方案時回應信任提示。 若要對方案授與信任，請使用確認為知名且受信任之發行者的憑證來簽署資訊清單。 請參閱透過 [簽署應用程式和部署資訊清單來信任解決方案](../vsto/granting-trust-to-office-solutions.md#Signing)。

 如果您要部署檔層級自訂，而且想要將檔放入使用者電腦上的資料夾中，或是在 SharePoint 網站上提供檔，請確定 Office 信任檔的位置。 請參閱 [授與信任給檔](../vsto/granting-trust-to-documents.md)。

## <a name="help-users-install-the-solution"></a><a name="Helping"></a> 協助使用者安裝解決方案
 使用者可以藉由執行安裝程式、開啟部署資訊清單，或在檔層級自訂期間直接開啟檔，來安裝解決方案。 最理想的做法是使用者應使用安裝程式安裝您的方案。 其他兩種方法不確定已安裝先決條件軟體。 如果使用者想要從安裝位置開啟文件，則必須將文件加入至 Office 應用程式的 [信任中心] 中信任的位置清單。

### <a name="opening-the-document-of-a-document-level-customization"></a>開啟文件層級自訂的文件
 使用者可以直接從安裝位置開啟文件層級自訂的文件，或是將文件複製到其本機電腦，然後開啟複本。

 最理想的做法是使用者應該在其電腦上開啟文件的複本，如此就不會有多位使用者嘗試同時開啟相同的複本。 若要強制執行這種做法，您可以設定安裝程式將文件複製到使用者電腦。 請參閱 [將解決方案的檔放在終端使用者的電腦上 (檔層級自訂僅) ](#Put)。

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>從 IIS 網站開啟部署資訊清單，以安裝解決方案
 使用者可以從 Web 開啟部署資訊清單，藉此安裝 Office 方案。 不過，Internet Information Services (IIS) 的安全安裝將會封鎖副檔名為 *.vsto* 的檔案。 您必須先在 IIS 中定義 MIME 類型，才能使用 IIS 部署 Office 方案。

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>若要將 .vsto MIME 類型加入至 IIS 6.0

1. 在執行 iis 6.0 的伺服器上，選擇 [**啟動**  >  **所有程式**] 系統  >  **管理工具**  >   **Internet Information Services (IIS) 管理員**。

2. 選擇 [電腦名稱稱]、[ **網站** ] 資料夾或您正在設定的網站。

3. 在功能表列上，選擇 [**動作**  >  **屬性**]。

4. 在 [ **HTTP 標頭** ] 索引標籤上，選擇 [ **MIME 類型** ] 按鈕。

5. 在 [ **MIME 類型** ] 視窗中，選擇 [ **新增** ] 按鈕。

6. 在 [ **MIME 類型** ] 視窗中，輸入 **.vsto** 做為副檔名，並輸入 **application/x-ms-vsto** 作為 MIME 類型，然後套用新的設定。

    > [!NOTE]
    > 您必須重新啟動 World Wide Web Publishing 服務，或等待背景工作處理序回收，變更才會生效。 接著，您必須排清瀏覽器的磁碟快取，然後再次嘗試開啟 *vsto* 檔案。

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>若要將 .vsto MIME 類型加入至 IIS 7.0

1. 在執行 IIS 7.0 的伺服器上，選擇 [**啟動**  >  **所有程式**  >  **附屬** 應用程式]。

2. 開啟 [ **命令提示** 字元] 的快捷方式功能表，然後選擇 [以  **系統管理員身分執行]。**

3. 在 [ **開啟** ] 方塊中，輸入下列路徑，然後選擇 [ **確定]** 按鈕。

    ```cmd
    %windir%\system32\inetsrv
    ```

4. 輸入下列命令，然後套用新的設定。

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > 您必須重新啟動 World Wide Web Publishing 服務，或是等待背景工作處理序回收，變更才會生效。 接著，您必須排清瀏覽器的磁碟快取，然後再次嘗試開啟 *vsto* 檔案。

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a> 將方案的檔放在終端使用者的電腦上 (檔層級自訂，只) 
 您可以藉由建立部署後動作，將解決方案的檔案複製到使用者的電腦上。 如此一來，使用者就不需要在安裝您的解決方案之後，手動將檔從安裝位置複製到電腦上。 您必須建立定義部署後動作的類別、建立和發佈方案、修改應用程式資訊清單，以及重新簽署應用程式和部署資訊清單。

 下列程式假設您的專案名稱為 **ExcelWorkbook** ，且您將解決方案發佈至您電腦上名為 **C:\publish** 的已建立資料夾中。

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>建立定義部署後動作的類別

1. 在功能表列上 **，選擇 [** 檔案  >  **加入**  >  **新專案**]。

2. 在 [ **加入新專案** ] 對話方塊的 [ **已安裝的範本** ] 窗格中，選擇 [ **Windows** ] 資料夾。

3. 在 [ **範本** ] 窗格中，選擇 [ **類別庫** ] 範本。

4. 在 [ **名稱** ] 欄位中，輸入 **FileCopyPDA**，然後選擇 [ **確定]** 按鈕。

5. 在 **方案總管** 中，選擇 [ **FileCopyPDA** ] 專案。

6. 在功能表列上，選擇 [**專案**  >  **加入參考**]。

7. 在 [ **.net** ] 索引標籤上，加入和的參考 `Microsoft.VisualStudio.Tools.Applications.Runtime` `Microsoft.VisualStudio.Tools.Applications.ServerDocument` 。

8. 將類別重新命名為 `FileCopyPDA`，然後將檔案的內容取代為程式碼。 此程式碼會執行下列工作：

   - 將文件複製到使用者的桌面。

   - 將 _AssemblyLocation 屬性從相對路徑變更為部署資訊清單的完整路徑。

   - 如果使用者解除安裝方案，則將檔案刪除。

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs" id="Snippet7":::

### <a name="build-and-publish-the-solution"></a>建置及發行方案

1. 在 **方案總管** 中，開啟 **FileCopyPDA** 專案的快捷方式功能表，然後選擇 [ **組建**]。

2. 開啟 **ExcelWorkbook** 專案的快捷方式功能表，然後選擇 [ **建立**]。

3. 開啟 **ExcelWorkbook** 專案的快捷方式功能表，然後選擇 [ **加入參考**]。

4. 在 [ **加入參考** ] 對話方塊中，選擇 [ **專案** ] 索引標籤，選擇 [ **FileCopyPDA**]，然後選擇 [ **確定]** 按鈕。

5. 在 **方案總管** 中，選擇 [ **ExcelWorkbook** ] 專案。

6. 在功能表列上，選擇 [**專案**  >  **新資料夾**]。

7. 輸入 **資料**，然後選擇 **enter** 鍵。

8. 在 **方案總管** 中，選擇 [ **Data** ] 資料夾。

9. 在功能表列上，選擇 [**專案**  >  **加入現有專案**]。

10. 在 [ **加入現有專案** ] 對話方塊中，流覽至 **ExcelWorkbook** 專案的輸出目錄，選擇 **ExcelWorkbook.xlsx** 檔案，然後選擇 [ **加入** ] 按鈕。

11. 在 **方案總管** 選擇 **ExcelWorkbook.xlsx** 檔。

12. 在 [ **屬性** ] 視窗中，將 [ **組建動作** ] 屬性變更為 [ **內容** ]，並將 [ **複製到輸出目錄** ] 屬性變更為 [已 **更新**]。

     當您完成這些步驟之後，您的專案就會類似下圖。

     ![部署後動作的專案結構。](../vsto/media/vsto-postdeployment.png "部署後動作的專案結構。")

13. 發佈 **ExcelWorkbook** 專案。

### <a name="modify-the-application-manifest"></a>修改應用程式資訊清單

1. 使用 **檔案總管** 開啟方案目錄（ **c:\publish**）。

2. 開啟 [ **應用程式檔** ] 資料夾，然後開啟對應至最新發行之方案版本的資料夾。

3. 在文字編輯器（例如 [記事本]）中開啟 **ExcelWorkbook.dll 的資訊清單** 檔。

4. 在 `</vstav3:update>` 項目後面加上下列程式碼。 若為專案的類別屬性 `<vstav3:entryPoint>` ，請使用下列語法： *NamespaceName。* 在下列範例中，命名空間和類別名稱相同，因此產生的進入點名稱是 `FileCopyPDA.FileCopyPDA`。

    ```xml
    <vstav3:postActions>
      <vstav3:postAction>
        <vstav3:entryPoint
          class="FileCopyPDA.FileCopyPDA">
          <assemblyIdentity
            name="FileCopyPDA"
            version="1.0.0.0"
            language="neutral"
            processorArchitecture="msil" />
        </vstav3:entryPoint>
        <vstav3:postActionData>
        </vstav3:postActionData>
      </vstav3:postAction>
    </vstav3:postActions>
    ```

### <a name="re-sign-the-application-and-deployment-manifests"></a>重新簽署應用程式和部署資訊清單

1. 在 **%USERPROFILE%\Documents\Visual Studio 2013 \ Projects\ExcelWorkbook\ExcelWorkbook** 資料夾中，複製 **ExcelWorkbook_TemporaryKey 的 .pfx** 憑證檔案，然後將它貼到 *PublishFolder* **\Application Files\ExcelWorkbook** \_ _MostRecentPublishedVersion_ 資料夾中。

2. 開啟 Visual Studio 命令提示字元，然後將目錄變更為 **c:\publish\Application Files\ExcelWorkbook** \_ _MostRecentPublishedVersion_ 資料夾 (例如 **c:\publish\Application Files \ ExcelWorkbook_1_0_0_4**) 。

3. 執行下列命令簽署修改後的應用程式資訊清單：

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     「ExcelWorkbook.dll.manifest 簽署成功」訊息隨即顯示。

4. 切換至 **c:\publish** 資料夾，然後執行下列命令來更新和簽署部署資訊清單：

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > 在上述範例中，請將 MostRecentVersionNumber 取代為您解決方案的最新發行版本的版本號碼 (例如 **1_0_0_4**) 。

     「ExcelWorkbook.vsto 簽署成功」訊息隨即顯示。

5. 將 *ExcelWorkbook vsto* 檔複製到 **c:\publish\Application Files\ExcelWorkbook** \_ _MostRecentVersionNumber_ 目錄。

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a> 將方案的檔放置到執行 SharePoint 的伺服器上 (檔層級的自訂) 
 您可以使用 SharePoint 將文件層級自訂發行至終端使用者。 當使用者前往 SharePoint 網站並開啟文件時，執行階段會自動將共用網路資料夾中的方案安裝到使用者的本機電腦。 方案安裝到本機上之後，即使文件是複製到其他地方 (例如桌面)，自訂仍舊會執行。

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>若要將文件放置到執行 SharePoint 的伺服器上

1. 將方案文件加入至 SharePoint 網站上的文件庫。

2. 執行下列其中一種方法的步驟：

    - 使用 Office 組態工具將執行 SharePoint 的伺服器加入至所有使用者電腦上 Word 或 Excel 中的 [信任中心]。

         請參閱 [Office 2010 中的安全性原則和設定](/previous-versions/office/office-2010/cc178946(v=office.14))。

    - 確定每位使用者都執行下列步驟。

        1. 在本機電腦上，開啟 [ **Word] 或 [Excel** ]，選擇 [檔案] 索引標籤，然後選擇 [ **選項** ] 按鈕。

        2. 在 [ **信任中心** ] 對話方塊中，選擇 [ **信任位置** ] 按鈕。

        3. 選取 [ **允許我的網路上的受信任位置 (不建議使用)** ] 核取方塊，然後選擇 [ **新增位置** ] 按鈕。

        4. 在 [ **路徑** ] 方塊中，輸入包含您上傳之檔的 SharePoint 文件庫 URL (例如 *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*) 。

             請勿加入預設網頁的名稱，例如 *default.aspx* 或 *allitems.aspx .aspx*。

        5. 選取 [ **同時信任此位置的子資料夾** ] 核取方塊，然後選擇 [ **確定]** 按鈕。

             當使用者從 SharePoint 網站開啟文件時，文件隨即開啟，而且會安裝自訂。 使用者可以將文件複製到桌面。 自訂仍舊會執行，因為文件中的屬性是指向文件的網路位置。

## <a name="create-a-custom-installer"></a><a name="Custom"></a> 建立自訂安裝程式
 您可以為 Office 方案建立自訂安裝程式，而不是在發行方案時使用為您建立的安裝程式。 例如，您可以使用登入腳本來開始安裝，或者您可以使用批次檔來安裝解決方案，而不需要使用者互動。 使用者電腦上已安裝必要條件時，下列情境可獲得最佳效果。

 在您的自訂安裝程式中，呼叫 Office 方案的安裝程式工具 (*VSTOInstaller.exe*) ，預設會安裝在下列位置：

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 如果工具不在該位置中，您可以使用 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath** 或 **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath** 登錄機碼來尋找該工具的路徑。

 您可以搭配 *VSTOinstaller.exe* 使用下列參數。

| 參數 | 定義 |
|------------------| - |
| /Install 或 /I | 安裝方案。 這個選項後面必須接著部署資訊清單的路徑。 您可以指定本機電腦上的路徑，也就是通用命名慣例 (UNC) 檔案共用。 您可以指定本機路徑 (*C:\FolderName\PublishFolder*) 、 (*發行 \\*) 的相對路徑，或 (*\\ \ServerName\FolderName* 或 HTTP://<em>ServerName/資料夾名稱</em>) 的完整位置。 |
| /Uninstall 或 /U | 解除安裝方案。 這個選項後面必須接著部署資訊清單的路徑。 您可以指定位於本機電腦或 UNC 檔案共用上的路徑。 您可以指定本機路徑 (*c:\FolderName\PublishFolder*) 、 (*發行 \\*) 的相對路徑，或 (*\\ \ServerName\FolderName* 或 HTTP://<em>ServerName/資料夾名稱</em>) 的完整位置。 |
| /Silent 或 /S | 在不提示使用者輸入或顯示任何訊息的情況下，進行安裝或解除安裝。 如果需要信任提示，則不會安裝或更新自訂。 |
| /Help 或 /? | 顯示 [說明] 資訊。 |

 當您執行 *VSTOinstaller.exe* 時，可能會出現下列錯誤碼。

|錯誤碼|定義|
|----------------|----------------|
|0|方案已成功安裝或解除安裝，或是出現 VSTOInstaller [說明]。|
|-100|一或多個命令列選項無效或設定了一次以上。 如需詳細資訊，請輸入 "vstoinstaller/？" 或者，請參閱 [建立 ClickOnce Office 方案的自訂安裝程式](/previous-versions/bb772078(v=vs.110))。|
|-101|一或多個命令列選項無效。 如需詳細資訊，請輸入 "vstoinstaller /?"。|
|-200|部署資訊清單 URI 無效。 如需詳細資訊，請輸入 "vstoinstaller /?"。|
|-201|無法安裝解決方案，因為部署資訊清單無效。 請參閱 [Office 方案的部署資訊清單](../vsto/deployment-manifests-for-office-solutions.md)。|
|-202|無法安裝解決方案，因為應用程式資訊清單的 Visual Studio Tools for Office 區段無效。 請參閱 [Office 方案的應用程式資訊清單](../vsto/application-manifests-for-office-solutions.md)。|
|-203|無法安裝解決方案，因為發生下載錯誤。 請檢查部署資訊清單的 URI 或網路檔案的位置，然後再試一次。|
|-300|無法安裝解決方案，因為發生安全性例外狀況。 請參閱 [安全的 Office 方案](../vsto/securing-office-solutions.md)。|
|-400|無法安裝解決方案。|
|-401|無法卸載方案。|
|-500|作業已取消，因為無法安裝或解除安裝方案，或是無法下載部署資訊清單。|

## <a name="publish-an-update"></a><a name="Update"></a> 發佈更新
 若要更新方案，請使用 [ **專案設計** 工具] 或 [ **發佈嚮導]** 再次發行，然後將更新的解決方案複製到安裝位置。 將檔案複製到安裝位置時，務必覆寫先前的檔案。

 下次解決方案檢查是否有更新時，會自動尋找並載入新的版本。

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a> 變更方案的安裝位置
 您可以在發行方案之後，加入或變更安裝路徑。 基於下列其中一個或多個原因，您可能會想要變更安裝路徑：

- 在知道安裝路徑之前就已編譯安裝程式。

- 方案檔案已複製至不同位置。

- 裝載安裝檔案的伺服器換了名稱或位置。

  若要變更方案的安裝路徑，您必須更新安裝程式，然後使用者必須執行安裝程式。 若是文件層級自訂，使用者也必須更新其文件中的屬性，以指向新位置。

> [!NOTE]
> 如果您不想要要求使用者更新其檔內容，您可以要求使用者從安裝位置取得更新的檔。

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>若要變更安裝程式中的安裝路徑

1. 開啟 [ **命令提示** 字元] 視窗，然後將目錄變更為安裝資料夾。

2. 執行安裝程式並且包含 `/url` 參數，這個參數會將新安裝路徑當成字串。

    下列範例將示範如何將安裝路徑變更為 Fabrikam 網站上的位置，不過您可以將 URL 取代為您要的路徑：

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > 如果出現訊息並指出可執行檔的簽章將失效，則用來簽署方案的憑證將不再有效且發行者為未知。 如此一來，使用者就必須確認可以信任方案的來源，才能進行安裝。

   > [!NOTE]
   > 若要顯示目前的 URL 值，請執行 `setup.exe /url`。

   若為檔層級自訂，使用者必須開啟檔，然後更新其 _AssemblyLocation 屬性。 下列步驟將描述使用者如何執行這項工作。

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>若要更新文件中的 _AssemblyLocation 屬性

1. **在 [檔案] 索引** 標籤上，選擇 [**資訊**]，如下圖所示。

     ![Excel 中的 [資訊] 索引標籤](../vsto/media/vsto-infotab.png "Excel 中的 [資訊] 索引標籤")

2. 在 [ **屬性** ] 清單中，選擇 [ **Advanced Properties**]，如下圖所示。

     ![Excel 中的 [進階屬性]。](../vsto/media/vsto-advanceddocumentproperties.png "Excel 中的 [進階屬性]。")

3. 在 [**屬性**] 清單的 [**自訂**] 索引標籤上，選擇 [_AssemblyLocation]，如下圖所示。

     ![AssemblyLocation 屬性。](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation 屬性。")

     [ **值** ] 方塊包含部署資訊清單識別碼。

4. 在識別碼前面輸入檔的完整路徑，後面接著一個橫條，格式 *路徑* | *識別碼* (例如 *File://ServerName/FolderName/FileName|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*。

     如需有關如何格式化此識別碼的詳細資訊，請參閱 [自訂文件屬性總覽](../vsto/custom-document-properties-overview.md)。

5. 選擇 [ **確定]** 按鈕，然後儲存並關閉檔。

6. 執行不含 /url 參數的安裝程式，在指定的位置安裝方案。

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a> 將解決方案復原至較早的版本
 當您復原方案時，可以將使用者還原為該方案的舊版。

#### <a name="to-roll-back-a-solution"></a>若要復原方案

1. 開啟方案的安裝位置。

2. 在最上層的 [發佈] 資料夾中，)  (的 *vsto* 檔案刪除部署資訊清單。

3. 尋找要復原之版本的子資料夾。

4. 將部署資訊清單從該資料夾複製至最上層發行資料夾。

     例如，若要將稱為 **為 outlookaddin1 方案** 的方案從版本1.0.0.1 復原至1.0.0.0 版，請從 **OutlookAddIn1_1_0_0_0** 資料夾複製檔案 **為 outlookaddin1 方案。** 將檔案貼到最上層的 [發行] 資料夾，覆寫已存在的 **OutlookAddIn1_1_0_0_1** 的版本特定部署資訊清單。

     下圖顯示這個範例中的發行資料夾結構。

     ![發行資料夾結構](../vsto/media/publishfolderstructure.png "發行資料夾結構")

     下次使用者開啟應用程式或自訂文件時，就會偵測到部署資訊清單的變更。 舊版 Office 方案便會從 ClickOnce 快取中執行。

> [!NOTE]
> 任何方案都只有前一個版本會儲存為本機資料。 如果您復原兩個版本，則不會保留本機資料。 如需本機資料的詳細資訊，請參閱 [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。

## <a name="see-also"></a>另請參閱

- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
- [發佈 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [如何：使用 ClickOnce 發行 Office 方案](/previous-versions/bb386095(v=vs.110))
- [如何：安裝 ClickOnce Office 方案](/previous-versions/bb608592(v=vs.110))
- [如何：使用 ClickOnce 將檔層級 Office 方案發行至 SharePoint 伺服器](/previous-versions/bb608595(v=vs.110))
- [建立 ClickOnce office 方案的自訂安裝程式](/previous-versions/bb772078(v=vs.110))