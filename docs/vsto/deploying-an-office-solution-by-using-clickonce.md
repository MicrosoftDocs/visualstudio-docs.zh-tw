---
title: 使用 ClickOnce 部署 Office 解決方案
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4adbd08d13d26c717beeb454bd323185bb88640
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416558"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>使用 ClickOnce 部署 Office 解決方案
  使用 ClickOnce 只需要幾個步驟就能部署 Office 方案。 如果您發行更新，方案會自動偵測並安裝更新。 不過，ClickOnce 要求您針對電腦上的每個使用者分別安裝方案。 因此，如果多個使用者將在同一台電腦上運行您的解決方案，則應考慮使用 Windows 安裝程式 *（.msi*）。

## <a name="in-this-topic"></a>本主題內容

- [發行方案](#Publish)

- [決定您想要將信任授與方案的方式](#Trust)

- [協助使用者安裝方案](#Helping)

- [將方案的文件放置到使用者的電腦上 (僅適用於文件層級自訂)](#Put)

- [將方案的文件放置到執行 SharePoint 的伺服器上 (僅適用於文件層級自訂)](#SharePoint)

- [創建自訂安裝程式](#Custom)

- [發行更新](#Update)

- [變更方案的安裝位置](#Location)

- [將方案復原為舊版](#Roll)

  有關如何通過創建 Windows 安裝程式檔部署 Office 解決方案的詳細資訊，請參閱使用[Windows 安裝程式部署 Office 解決方案](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)。

## <a name="publish-the-solution"></a><a name="Publish"></a>發佈解決方案
 您可以使用**發佈嚮導**或**專案設計器**發佈解決方案。 在此過程中，您將使用**專案設計器**，因為它提供了完整的發佈選項組。 請參閱[在視覺化工作室&#41;中發佈嚮導&#40;辦公室開發](../vsto/publish-wizard-office-development-in-visual-studio.md)。

#### <a name="to-publish-the-solution"></a>若要發行方案

1. 在**解決方案資源管理器中**，選擇為專案命名的節點。

2. 在功能表列上，選擇 **"專案**"，*專案名稱***屬性**。

3. 在 **"專案設計器**"中，選擇 **"發佈**"選項卡，如下圖所示。

    ![[專案設計工具] 中的 [發行] 索引標籤](../vsto/media/vsto-publishtab.png "[專案設計工具] 中的 [發行] 索引標籤")

4. 在 **"發佈資料夾位置（ftp 伺服器或檔路徑）"** 框中，輸入希望**專案設計器**複製解決方案檔的資料夾的路徑。

    您可以輸入下列任何類型的路徑。

   - 本地路徑（例如 *，C：\資料夾名稱\資料夾名稱*）。

   - 到網路上的資料夾（例如*\\，[伺服器名稱]資料夾名稱*）的統一命名約定 （UNC） 路徑。

   - 相對路徑（例如 *，PublishFolder\\*，這是預設情況下將專案發佈到其中的資料夾）。

5. 在 **"安裝資料夾 URL"** 框中，輸入最終使用者將找到解決方案的位置的完全限定路徑。

    如果您還不知道位置，請不要在此欄位中輸入任何內容。 根據預設，ClickOnce 會在您的使用者安裝方案的資料夾中尋找更新。

6. 選擇 [ **必要條件** ] 按鈕。

7. 在 **"先決條件"** 對話方塊中，確保選中"**創建安裝程式以安裝必備元件**"核取方塊。

8. 在 **"選擇安裝哪些先決條件**"清單中，選擇 Windows 安裝程式**4.5**和相應的 .NET 框架包的核取方塊。

    例如，如果解決方案以 ，[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]選擇 Windows 安裝程式**4.5**和**Microsoft .NET 框架 4.5 已滿**的核取方塊。

9. 如果解決方案以 .NET 框架 4.5 為目標，請選擇 **"視覺化工作室 2010 Office 運行時工具**"核取方塊。

    > [!NOTE]
    > 預設情況下，此核取方塊不會顯示。 若要顯示這個核取方塊，您必須建立啟動載入器套件。 請參閱[為 Office 2013 VSTO 外接程式創建一個引導套裝程式，該載入程式與 Visual Studio 2012](create-vsto-add-ins-for-office-by-using-visual-studio.md)一起。

10. 在 **"為先決條件指定安裝位置"** 下，選擇顯示的選項之一，然後選擇 **"確定**"按鈕。

     下表會說明每個選項。

    |選項|描述|
    |------------|-----------------|
    |**從元件廠商的網站下載必要條件**|系統會提示使用者下載並安裝廠商提供的這些必要條件。|
    |**從應用程式的相同位置下載必要條件**|必要軟體會隨方案安裝。 如果您選擇這個選項，Visual Studio 會自動將所有必要條件套件複製到發行位置。 必要條件套件必須放在開發電腦上，這個選項才能正常運作。|
    |**從下列位置下載必要條件**|Visual Studio 會將所有必要條件套件複製到您指定的位置，並且隨方案安裝這些套件。|

     請參閱[先決條件對話方塊](../ide/reference/prerequisites-dialog-box.md)。

11. 選擇 **"更新**"按鈕，指定希望每個最終使用者的 VSTO 外接程式或自訂值檢查更新的頻率，然後選擇 **"確定**"按鈕。

    > [!NOTE]
    > 如果使用 CD 或卸除式磁碟機進行部署，請選擇 **"從不檢查更新**"選項按鈕。

     有關如何發佈更新的資訊，請參閱[發佈更新](#Update)。

12. 選擇 **"選項**"按鈕，查看"**選項**"對話方塊中的選項，然後選擇 **"確定**"按鈕。

13. 選擇"**立即發佈"** 按鈕。

     Visual Studio 會將下列資料夾和檔案加入至您在本程序前段指定的發行資料夾。

    - **應用程式檔**資料夾。

    - 安裝程式。

    - 部署資訊清單，會指向最新版本的部署資訊清單。

      "**應用程式檔**"資料夾包含發佈的每個版本的子資料夾。 每個版本專屬子資料夾都包含下列檔案。

    - 應用程式資訊清單。

    - 部署資訊清單。

    - 自訂組件。

      下圖顯示 Outlook VSTO 增益集的發行資料夾結構。

      ![發佈資料夾結構](../vsto/media/publishfolderstructure.png "發行資料夾結構")

    > [!NOTE]
    > 按一下"一次"將 *.deploy*副檔名追加到程式集，以便安全安裝 Internet 資訊服務 （IIS） 不會因為不安全的擴展而阻止檔。 當使用者安裝解決方案時，按一下"一次"將刪除 *.deploy*副檔名。

14. 將方案檔複製到您在本程序前段指定的安裝位置。

## <a name="decide-how-you-want-to-grant-trust-to-the-solution"></a><a name="Trust"></a>決定如何授予解決方案的信任
 在使用者電腦上執行方案之前，您必須先授與信任，或是使用者必須在安裝方案時回應信任提示。 若要對方案授與信任，請使用確認為知名且受信任之發行者的憑證來簽署資訊清單。 請參閱[通過簽署應用程式和部署清單來信任解決方案](../vsto/granting-trust-to-office-solutions.md#Signing)。

 如果要部署文檔級自訂，並且希望將文檔放入使用者電腦上的資料夾中或在 SharePoint 網站上提供文檔，請確保 Office 信任文檔的位置。 請參閱[授予對文檔的信任](../vsto/granting-trust-to-documents.md)。

## <a name="help-users-install-the-solution"></a><a name="Helping"></a>説明使用者安裝解決方案
 使用者可以通過運行安裝程式、打開部署清單或在文檔級自訂期間直接打開文檔來安裝解決方案。 最理想的做法是使用者應使用安裝程式安裝您的方案。 其他兩種方法不確保安裝必備軟體。 如果使用者想要從安裝位置開啟文件，則必須將文件加入至 Office 應用程式的 [信任中心] 中信任的位置清單。

### <a name="opening-the-document-of-a-document-level-customization"></a>開啟文件層級自訂的文件
 使用者可以直接從安裝位置開啟文件層級自訂的文件，或是將文件複製到其本機電腦，然後開啟複本。

 最理想的做法是使用者應該在其電腦上開啟文件的複本，如此就不會有多位使用者嘗試同時開啟相同的複本。 若要強制執行這種做法，您可以設定安裝程式將文件複製到使用者電腦。 請參閱[將解決方案的文檔放在最終使用者的電腦（僅限文檔級自訂）上](#Put)。

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>通過從 IIS 網站打開部署清單來安裝解決方案
 使用者可以從 Web 開啟部署資訊清單，藉此安裝 Office 方案。 但是，安全安裝 Internet 資訊服務 （IIS） 將阻止具有 *.vsto*副檔名的檔。 您必須先在 IIS 中定義 MIME 類型，才能使用 IIS 部署 Office 方案。

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>若要將 .vsto MIME 類型加入至 IIS 6.0

1. 在運行 IIS 6.0 的伺服器上，選擇 **"啟動** > **所有程式** > **管理工具** >  **互聯網資訊服務 （IIS） 管理器**"。

2. 選擇要配置的電腦名稱稱、**網站**資料夾或網站。

3. 在功能表列上，選擇**操作** > **屬性**。

4. 在**HTTP 標題**選項卡上，選擇**MIME 類型**按鈕。

5. 在**MIME 類型**視窗中，選擇 **"新建"** 按鈕。

6. 在**MIME 類型**視窗中，輸入 **.vsto**作為擴展，輸入**應用程式/x-ms-vsto**作為 MIME 類型，然後應用新設置。

    > [!NOTE]
    > 您必須重新啟動 World Wide Web Publishing 服務，或等待背景工作處理序回收，變更才會生效。 然後，必須刷新瀏覽器的磁片緩存，然後嘗試再次打開 *.vsto*檔。

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>若要將 .vsto MIME 類型加入至 IIS 7.0

1. 在運行 IIS 7.0 的伺服器上，選擇 **"啟動** > **所有程式** > **附件**"。

2. 打開**命令提示**符的快顯功能表，然後選擇 **"以管理員身份運行"。**

3. 在 **"打開"** 框中，輸入以下路徑，然後選擇 **"確定**"按鈕。

    ```cmd
    %windir%\system32\inetsrv
    ```

4. 輸入下列命令，然後套用新的設定。

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']
    ```

    > [!NOTE]
    > 您必須重新啟動 World Wide Web Publishing 服務，或是等待背景工作處理序回收，變更才會生效。 然後，必須刷新瀏覽器的磁片緩存，然後嘗試再次打開 *.vsto*檔。

## <a name="put-the-document-of-a-solution-onto-the-end-users-computer-document-level-customizations-only"></a><a name="Put"></a>將解決方案的文檔放在最終使用者的電腦上（僅限文檔級自訂）
 您可以通過創建部署後動作將解決方案的文檔複製到最終使用者的電腦中。 這樣，使用者在安裝解決方案後不必手動將文檔從安裝位置複製到電腦。 您必須創建一個類來定義部署後動作、生成和發佈解決方案、修改應用程式清單以及重新簽名應用程式和部署清單。

 以下過程假定專案名稱為**ExcelWorkbook，** 並且將解決方案發佈到電腦上名為**C：\發佈**創建的資料夾中。

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>建立定義部署後動作的類別

1. 在功能表列上，選擇 **"檔** > **添加新** > **專案**"。

2. 在"**添加新專案**"對話方塊中，在 **"已安裝範本"** 窗格中，選擇**Windows**資料夾。

3. 在 **"範本"** 窗格中，選擇**類庫**範本。

4. 在 **"名稱"** 欄位中，輸入**檔CopyPDA，** 然後選擇 **"確定**"按鈕。

5. 在**解決方案資源管理器中**，選擇**檔案複製PDA**專案。

6. 在功能表列上，選擇 **"專案** > **添加參考**"。

7. 在 **.NET**選項卡上，添加`Microsoft.VisualStudio.Tools.Applications.Runtime``Microsoft.VisualStudio.Tools.Applications.ServerDocument`對 和 的引用。

8. 將類別重新命名為 `FileCopyPDA`，然後將檔案的內容取代為程式碼。 此程式碼會執行下列工作：

   - 將文件複製到使用者的桌面。

   - 將_AssemblyLocation屬性從相對路徑更改為部署清單的完全限定路徑。

   - 如果使用者解除安裝方案，則將檔案刪除。

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]

### <a name="build-and-publish-the-solution"></a>建置及發行方案

1. 在**解決方案資源管理器**中，打開**FileCopyPDA**專案的快顯功能表，然後選擇 **"生成**"。

2. 打開**ExcelWorkbook**專案的快顯功能表，然後選擇 **"生成**"。

3. 打開**ExcelWorkbook**專案的快顯功能表，然後選擇 **"添加參考**"。

4. 在"**添加參考**"對話方塊中，選擇"**專案**"選項卡，選擇 **"檔CopyPDA"，** 然後選擇"**確定**"按鈕。

5. 在**解決方案資源管理器**中，選擇**ExcelWorkbook**專案。

6. 在功能表列上，選擇 **"專案** > **新資料夾**"。

7. 輸入**資料**，然後選擇**Enter**鍵。

8. 在**解決方案資源管理器中**，選擇 **"資料**"資料夾。

9. 在功能表列上，選擇 **"專案** > **添加現有專案**"。

10. 在"**添加現有專案"** 對話方塊中，流覽到**ExcelWorkbook**專案的輸出目錄，選擇**ExcelWorkbook.xlsx**檔，然後選擇"**添加**"按鈕。

11. 在**解決方案資源管理器**中選擇**ExcelWorkbook.xlsx**檔。

12. 在 **"屬性"** 視窗中，將 **"生成操作"** 屬性更改為 **"內容**"，將 **"複製到輸出目錄"** 屬性更改為 **"如果更新，則複製到複製**"。

     完成這些步驟後，您的專案將類似于下圖。

     ![部署後動作的專案結構。](../vsto/media/vsto-postdeployment.png "部署後動作的專案結構。")

13. 發佈**ExcelWorkbook**專案。

### <a name="modify-the-application-manifest"></a>修改應用程式資訊清單

1. 使用**檔資源管理器**打開解決方案目錄**c：\發佈**。

2. 打開**應用程式檔**資料夾，然後打開與解決方案的最新版本對應的資料夾。

3. 在文字編輯器（如記事本）中打開**ExcelWorkbook.dll.清單**檔。

4. 在 `</vstav3:update>` 項目後面加上下列程式碼。 對於元素的類屬性，`<vstav3:entryPoint>`請使用以下語法 *：NamespaceName.classname*。 在下列範例中，命名空間和類別名稱相同，因此產生的進入點名稱是 `FileCopyPDA.FileCopyPDA`。

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

1. 在 **%USERPROFILE%%\文檔\Visual Studio 2013_專案\ExcelWorkbook_ExcelWorkbook 資料夾中**，複製**ExcelWorkbook_TemporaryKey.pfx**證書檔，然後將其粘貼到 *"發佈資料夾***"[應用程式檔]ExcelWorkbook**\__最新發佈版本_資料夾中。

2. 打開 Visual Studio 命令提示符，然後將目錄更改為**c：\發佈\應用程式檔\ExcelWorkbook**\__最最近發佈版本_資料夾（例如 **，c：\發佈\應用程式檔\ExcelWorkbook_1_0_0_4）。**

3. 執行下列命令簽署修改後的應用程式資訊清單：

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx
    ```

     「ExcelWorkbook.dll.manifest 簽署成功」訊息隨即顯示。

4. 更改為**c：\publish**資料夾，然後通過運行以下命令更新和簽名部署清單：

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"
    ```

    > [!NOTE]
    > 在前面的示例中，將"最新版本編號"替換為解決方案最近發佈的版本的版本號（例如 **，1_0_0_4**）。

     「ExcelWorkbook.vsto 簽署成功」訊息隨即顯示。

5. 將*ExcelWorkbook.vsto*檔案複製到**c：\發佈\應用程式檔\ExcelWorkbook**\__最最新版本數_目錄。

## <a name="put-the-document-of-a-solution-onto-a-server-thats-running-sharepoint-document-level-customizations-only"></a><a name="SharePoint"></a>將解決方案的文檔放在運行 SharePoint 的伺服器上（僅限文檔級自訂）
 您可以使用 SharePoint 將文件層級自訂發行至終端使用者。 當使用者前往 SharePoint 網站並開啟文件時，執行階段會自動將共用網路資料夾中的方案安裝到使用者的本機電腦。 方案安裝到本機上之後，即使文件是複製到其他地方 (例如桌面)，自訂仍舊會執行。

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>若要將文件放置到執行 SharePoint 的伺服器上

1. 將方案文件加入至 SharePoint 網站上的文件庫。

2. 執行下列其中一種方法的步驟：

    - 使用 Office 組態工具將執行 SharePoint 的伺服器加入至所有使用者電腦上 Word 或 Excel 中的 [信任中心]。

         請參閱[Office 2010 中的安全性原則和設置](/previous-versions/office/office-2010/cc178946(v=office.14))。

    - 確定每位使用者都執行下列步驟。

        1. 在本地電腦上，打開 Word 或 Excel，選擇 **"檔**"選項卡，然後選擇"**選項**"按鈕。

        2. 在 **"信任中心**"對話方塊中，選擇 **"受信任的位置"** 按鈕。

        3. 選中"**允許信任的位置"核取方塊（不推薦），** 然後選擇"**添加新位置**"按鈕。

        4. 在 **"路徑"** 框中，輸入包含您上傳的文檔的 SharePoint 文件庫的 URL（例如。 *http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*

             不要添加預設網頁的名稱，如*預設.aspx*或*AllItem.aspx*。

        5. 選擇**此位置的子資料夾也是受信任的**核取方塊，然後選擇 **"確定**"按鈕。

             當使用者從 SharePoint 網站開啟文件時，文件隨即開啟，而且會安裝自訂。 使用者可以將文件複製到桌面。 自訂仍舊會執行，因為文件中的屬性是指向文件的網路位置。

## <a name="create-a-custom-installer"></a><a name="Custom"></a>創建自訂安裝程式
 您可以為 Office 解決方案創建自訂安裝程式，而不是在發佈解決方案時使用為您創建的安裝程式。 例如，可以使用登入指令檔啟動安裝，也可以使用批次檔安裝解決方案，而無需使用者交互。 使用者電腦上已安裝必要條件時，下列情境可獲得最佳效果。

 作為自訂安裝過程的一部分，請致電 Office 解決方案的安裝程式工具 *（VSTOInstaller.exe），* 該工具預設安裝在以下位置：

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*

 如果該工具不在該位置，您可以使用**HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VSTO 運行時設置\v4_安裝程式路徑**或**HKEY_LOCAL_MACHINE_SOFTWARE_Wow6432Node_Microsoft_VSTO 運行時設置\v4_安裝程式路徑**註冊表鍵來查找該工具的路徑。

 您可以將以下參數與*VSTO 安裝程式.exe*一起使用。

| 參數 | 定義 |
|------------------| - |
| /Install 或 /I | 安裝方案。 這個選項後面必須接著部署資訊清單的路徑。 您可以指定本機電腦上的路徑，也就是通用命名慣例 (UNC) 檔案共用。 您可以指定本地路徑 （*C：\資料夾名稱\發佈資料夾*）、相對路徑 （*發佈\\*） 或完全限定的位置 （*\\\ServerName_folderName*或 HTTP://<em>伺服器名稱/資料夾名稱</em>）。 |
| /Uninstall 或 /U | 解除安裝方案。 這個選項後面必須接著部署資訊清單的路徑。 您可以指定位於本機電腦或 UNC 檔案共用上的路徑。 您可以指定本地路徑 （*c：\folderName_發佈資料夾*）、相對路徑 （*發佈\\*） 或完全限定的位置 （*\\\ServerName_folderName*或HTTP://<em>伺服器名稱/資料夾名稱</em>）。 |
| /Silent 或 /S | 在不提示使用者輸入或顯示任何訊息的情況下，進行安裝或解除安裝。 如果需要信任提示，則不會安裝或更新自訂。 |
| /Help 或 /? | 顯示 [說明] 資訊。 |

 當您運行*VSTO 安裝程式.exe 時*，可能會出現以下錯誤代碼。

|錯誤碼|定義|
|----------------|----------------|
|0|方案已成功安裝或解除安裝，或是出現 VSTOInstaller [說明]。|
|-100|一個或多個命令列選項無效或設置多次。 有關詳細資訊，請輸入"vsto 安裝程式 /？" 或者，請參閱[為 ClickOnce Office 解決方案創建自訂安裝程式](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)。|
|-101|一個或多個命令列選項無效。 如需詳細資訊，請輸入 "vstoinstaller /?"。|
|-200|部署清單 URI 無效。 如需詳細資訊，請輸入 "vstoinstaller /?"。|
|-201|無法安裝解決方案，因為部署清單無效。 請參閱[Office 解決方案的部署清單](../vsto/deployment-manifests-for-office-solutions.md)。|
|-202|無法安裝解決方案，因為應用程式清單的"用於 Office 的視覺化工作室工具"部分無效。 請參閱[Office 解決方案的應用程式清單](../vsto/application-manifests-for-office-solutions.md)。|
|-203|無法安裝解決方案，因為發生下載錯誤。 請檢查部署資訊清單的 URI 或網路檔案的位置，然後再試一次。|
|-300|無法安裝解決方案，因為發生了安全異常。 請參閱[安全辦公室解決方案](../vsto/securing-office-solutions.md)。|
|-400|無法安裝解決方案。|
|-401|無法卸載解決方案。|
|-500|作業已取消，因為無法安裝或解除安裝方案，或是無法下載部署資訊清單。|

## <a name="publish-an-update"></a><a name="Update"></a>發佈更新
 要更新解決方案，請使用**專案設計器**或**發佈嚮導**再次發佈它，然後將更新的解決方案複製到安裝位置。 將檔案複製到安裝位置時，務必覆寫先前的檔案。

 下次解決方案檢查更新時，它將自動查找並載入新版本。

## <a name="change-the-installation-location-of-a-solution"></a><a name="Location"></a>更改解決方案的安裝位置
 您可以在發行方案之後，加入或變更安裝路徑。 基於下列其中一個或多個原因，您可能會想要變更安裝路徑：

- 在知道安裝路徑之前就已編譯安裝程式。

- 方案檔案已複製至不同位置。

- 裝載安裝檔案的伺服器換了名稱或位置。

  若要變更方案的安裝路徑，您必須更新安裝程式，然後使用者必須執行安裝程式。 若是文件層級自訂，使用者也必須更新其文件中的屬性，以指向新位置。

> [!NOTE]
> 如果不想要求使用者更新其文件屬性，可以要求使用者從安裝位置獲取更新的文檔。

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>若要變更安裝程式中的安裝路徑

1. 打開**命令提示視窗**，然後將目錄更改為安裝資料夾。

2. 執行安裝程式並且包含 `/url` 參數，這個參數會將新安裝路徑當成字串。

    下列範例將示範如何將安裝路徑變更為 Fabrikam 網站上的位置，不過您可以將 URL 取代為您要的路徑：

   ```cmd
   setup.exe /url="http://www.fabrikam.com/newlocation"
   ```

   > [!NOTE]
   > 如果出現訊息並指出可執行檔的簽章將失效，則用來簽署方案的憑證將不再有效且發行者為未知。 如此一來，使用者就必須確認可以信任方案的來源，才能進行安裝。

   > [!NOTE]
   > 若要顯示目前的 URL 值，請執行 `setup.exe /url`。

   對於文檔級自訂，使用者必須打開文檔，然後更新其_AssemblyLocation屬性。 下列步驟將描述使用者如何執行這項工作。

#### <a name="to-update-the-_assemblylocation-property-in-a-document"></a>若要更新文件中的 _AssemblyLocation 屬性

1. 在"**檔**"選項卡上，選擇下圖顯示**的資訊**。

     ![Excel 中的 [資訊] 索引標籤](../vsto/media/vsto-infotab.png "Excel 中的 [資訊] 索引標籤")

2. 在 **"屬性"** 清單中，選擇下圖顯示的高級**屬性**。

     ![Excel 中的 [進階屬性]。](../vsto/media/vsto-advanceddocumentproperties.png "Excel 中的 [進階屬性]。")

3. 在"**屬性"** 清單中的 **"自訂"** 選項卡上，選擇_AssemblyLocation，如下圖所示。

     ![AssemblyLocation 屬性。](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation 屬性。")

     **"值**"框包含部署清單識別碼。

4. 在識別碼之前，輸入文檔的完全限定路徑，後跟一個條形，*在格式路徑*|*識別碼*（例如 *，File://ServerName/FolderName/FileName|74744e4b-e4d6-41eb-84f7-ad20346fe2d9*。

     有關如何設置此識別碼格式的詳細資訊，請參閱[自訂文件屬性概述](../vsto/custom-document-properties-overview.md)。

5. 選擇 **"確定"** 按鈕，然後保存並關閉文檔。

6. 執行不含 /url 參數的安裝程式，在指定的位置安裝方案。

## <a name="roll-back-a-solution-to-an-earlier-version"></a><a name="Roll"></a>將解決方案回滾到早期版本
 當您復原方案時，可以將使用者還原為該方案的舊版。

#### <a name="to-roll-back-a-solution"></a>若要復原方案

1. 開啟方案的安裝位置。

2. 在頂級發佈資料夾中，刪除部署清單 *（.vsto*檔）。

3. 尋找要復原之版本的子資料夾。

4. 將部署資訊清單從該資料夾複製至最上層發行資料夾。

     例如，要將名為**OutlookAddIn1**的解決方案從版本 1.0.0.1 回滾到版本 1.0.0.0，請從**OutlookAddIn1_1_0_0_0**資料夾中複製檔**OutlookAddIn1.vsto。** 將檔粘貼到頂級發佈資料夾中，覆蓋已存在**OutlookAddIn1_1_0_0_1**的版本特定部署清單。

     下圖顯示這個範例中的發行資料夾結構。

     ![發佈資料夾結構](../vsto/media/publishfolderstructure.png "發行資料夾結構")

     下次使用者開啟應用程式或自訂文件時，就會偵測到部署資訊清單的變更。 舊版 Office 方案便會從 ClickOnce 快取中執行。

> [!NOTE]
> 任何方案都只有前一個版本會儲存為本機資料。 如果回滾兩個版本，則不會保留本地資料。 有關本地資料的詳細資訊，請參閱[ClickOnce 應用程式中訪問本地和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。

## <a name="see-also"></a>另請參閱

- [部署 Office 解決方案](../vsto/deploying-an-office-solution.md)
- [發佈 Office 解決方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [如何：使用 ClickOnce 發佈 Office 解決方案](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [操作方式：安裝 ClickOnce Office 解決方案](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)
- [如何：使用 ClickOnce 將文檔級 Office 解決方案發佈到 SharePoint 伺服器](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)
- [為 ClickOnce 辦公室解決方案創建自訂安裝程式](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)