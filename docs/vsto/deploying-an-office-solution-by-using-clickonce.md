---
title: 使用 ClickOnce 部署 Office 方案
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, deploying solutions
- ClickOnce deployment [Office development in Visual Studio], deploying solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e46a0bdc23ee16c4821d3da751d5a90aa62a14c3
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673064"
---
# <a name="deploy-an-office-solution-by-using-clickonce"></a>使用 ClickOnce 部署 Office 方案
  使用 ClickOnce 只需要幾個步驟就能部署 Office 方案。 如果您發行更新，方案會自動偵測並安裝更新。 不過，ClickOnce 要求您針對電腦上的每個使用者分別安裝方案。 因此，您應該考慮使用 Windows Installer (*.msi*) 如果一個以上的使用者將同一部電腦上執行您的解決方案。  

## <a name="in-this-topic"></a>本主題內容  

- [發行方案](#Publish)  

- [決定您要授與信任給方案的方式](#Trust)  

- [協助使用者安裝方案](#Helping)  

- [將方案文件放置到終端使用者的電腦 （文件層級自訂）](#Put)  

- [將方案文件放置到執行 SharePoint （文件層級自訂） 的伺服器](#SharePoint)  

- [建立自訂安裝程式](#Custom)  

- [發行更新](#Update)  

- [變更方案的安裝位置](#Location)  

- [將方案復原為舊版](#Roll)  

  如需如何建立 Windows Installer 檔案來部署 Office 方案的詳細資訊，請參閱[使用 Windows Installer 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-windows-installer.md)。  

##  <a name="Publish"></a> 發行方案  
 您可以使用，以便發行您的解決方案**發行精靈**或**專案設計工具**。 在此程序中，您將使用**專案設計工具**因為它提供一組完整的發行選項。 請參閱[發行精靈 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/publish-wizard-office-development-in-visual-studio.md)。  

#### <a name="to-publish-the-solution"></a>若要發行方案  

1. 在 [**方案總管] 中**，選擇您的專案名稱的節點。  

2. 在功能表列上選擇 **專案**， *ProjectName* **屬性**。  

3. 在 [**專案設計工具**，選擇**發佈**] 索引標籤，如下圖所示。  

    ![專案設計工具的 [發行] 索引標籤](../vsto/media/vsto-publishtab.png "專案設計工具的 [發行] 索引標籤")  

4. 在 **發行資料夾位置 （ftp 伺服器或檔案路徑）** 方塊中，輸入您想要的位置的資料夾路徑**專案設計工具**来複製的方案檔。  

    您可以輸入下列任何類型的路徑。  

   -   本機路徑 (例如*C:\FolderName\FolderName*)。  

   -   您的網路上的資料夾的統一命名慣例 (UNC) 路徑 (例如 *\\\ServerName\FolderName*)。  

   -   相對路徑 (例如*PublishFolder\\*，這是預設在其中發行專案的資料夾)。  

5. 在 **安裝資料夾 URL**方塊中，輸入終端使用者找到您的解決方案之位置的完整的路徑。  

    如果您不知道位置，但不要在此欄位輸入任何項目。 根據預設，ClickOnce 會在您的使用者安裝方案的資料夾中尋找更新。  

6. 選擇 [ **必要條件** ] 按鈕。  

7. 在 **必要條件**對話方塊方塊中，請確認**建立安裝程式以安裝必要條件元件**核取方塊已選取。  

8. 在 **選擇要安裝的必要條件**清單中，選取核取方塊**Windows Installer 4.5**和適當的.NET Framework 套件。  

    比方說，如果您的方案目標[!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]，選取核取方塊**Windows Installer 4.5**並**Microsoft.NET Framework 4.5 Full**。  

9. 如果您的解決方案是以.NET Framework 4.5 為目標，同時選取**Visual Studio 2010 Tools for Office Runtime**核取方塊。  

    > [!NOTE]  
    >  根據預設，不會出現此核取方塊。 若要顯示這個核取方塊，您必須建立啟動載入器套件。 請參閱[使用 Visual Studio 2012 建立的 Office 2013 VSTO 增益集啟動載入器套件](create-vsto-add-ins-for-office-by-using-visual-studio.md)。  

10. 底下**指定必要條件的安裝位置**，選擇其中一個選項，會出現，然後選擇**確定** 按鈕。  

     下表會說明每個選項。  

    |選項|描述|  
    |------------|-----------------|  
    |**從元件廠商的網站下載必要條件**|系統會提示使用者下載並安裝廠商提供的這些必要條件。|  
    |**從應用程式的相同位置下載必要條件**|必要軟體會隨方案安裝。 如果您選擇這個選項，Visual Studio 會自動將所有必要條件套件複製到發行位置。 必要條件套件必須放在開發電腦上，這個選項才能正常運作。|  
    |**從下列位置下載必要條件**|Visual Studio 會將所有必要條件套件複製到您指定的位置，並且隨方案安裝這些套件。|  

     請參閱[必要條件對話方塊](/visualstudio/ide/reference/prerequisites-dialog-box)。  

11. 選擇**更新**按鈕，指定您想每位使用者的 VSTO 增益集或自訂檢查更新，，然後選擇**確定** 按鈕。  

    > [!NOTE]  
    >  如果您要部署使用 CD 或卸除式磁碟機，請選擇**永遠不檢查更新**選項按鈕。  

     如需有關如何發行更新的資訊，請參閱 <<c0> [ 發行更新](#Update)。  

12. 選擇**選項**按鈕，檢閱中的選項**選項** 對話方塊的 ，然後選擇**確定**  按鈕。  

13. 選擇**立即發佈** 按鈕。  

     Visual Studio 會將下列資料夾和檔案加入至您在本程序前段指定的發行資料夾。  

    - **應用程式檔案**資料夾。  

    - 安裝程式。  

    - 部署資訊清單，會指向最新版本的部署資訊清單。  

      **應用程式檔案**資料夾包含您發行的每一個版本的子資料夾。 每個版本專屬子資料夾都包含下列檔案。  

    - 應用程式資訊清單。  

    - 部署資訊清單。  

    - 自訂組件。  

      下圖顯示 Outlook VSTO 增益集的發行資料夾結構。  

      ![發行資料夾結構](../vsto/media/publishfolderstructure.png "發行資料夾結構")  

    > [!NOTE]  
    >  ClickOnce 會附加 *.deploy*延伸模組組件，讓受保護的安裝網際網路資訊服務 (IIS) 將不會封鎖檔案，因為不安全的副檔名。 當使用者安裝方案時，ClickOnce 會移除 *.deploy*延伸模組。  

14. 將方案檔複製到您在本程序前段指定的安裝位置。  

##  <a name="Trust"></a> 決定您要授與信任給方案的方式  
 在使用者電腦上執行方案之前，您必須先授與信任，或是使用者必須在安裝方案時回應信任提示。 若要對方案授與信任，請使用確認為知名且受信任之發行者的憑證來簽署資訊清單。 請參閱[藉由簽署應用程式和部署資訊清單信任方案](../vsto/granting-trust-to-office-solutions.md#Signing)。  

 如果您要部署文件層級自訂，而且您想要將文件放入資料夾中，在使用者電腦上或 SharePoint 網站上提供文件，請確定 Office 信任文件的位置。 請參閱[授與信任給文件](../vsto/granting-trust-to-documents.md)。  

##  <a name="Helping"></a> 協助使用者安裝方案  
 使用者能夠安裝方案的方式包括：執行安裝程式、開啟部署資訊清單，或是在文件層級自訂的情況下直接開啟文件。 最理想的做法是使用者應使用安裝程式安裝您的方案。 其他兩種方法不確定已安裝的先決條件軟體。 如果使用者想要從安裝位置開啟文件，則必須將文件加入至 Office 應用程式的 [信任中心] 中信任的位置清單。  

### <a name="opening-the-document-of-a-document-level-customization"></a>開啟文件層級自訂的文件  
 使用者可以直接從安裝位置開啟文件層級自訂的文件，或是將文件複製到其本機電腦，然後開啟複本。  

 最理想的做法是使用者應該在其電腦上開啟文件的複本，如此就不會有多位使用者嘗試同時開啟相同的複本。 若要強制執行這種做法，您可以設定安裝程式將文件複製到使用者電腦。 請參閱[將方案文件放置到終端使用者的電腦 （文件層級自訂）](#Put)。  

### <a name="install-the-solution-by-opening-the-deployment-manifest-from-an-iis-website"></a>安裝解決方案，從 IIS 網站開啟部署資訊清單  
 使用者可以從 Web 開啟部署資訊清單，藉此安裝 Office 方案。 不過，受保護的安裝網際網路資訊服務 (IIS) 會封鎖所 *.vsto*延伸模組。 您必須先在 IIS 中定義 MIME 類型，才能使用 IIS 部署 Office 方案。  

##### <a name="to-add-the-vsto-mime-type-to-iis-60"></a>若要將 .vsto MIME 類型加入至 IIS 6.0  

1.  在執行 IIS 6.0 伺服器上，選擇**開始** > **所有程式** > **系統管理工具** >   **Internet Information Services (IIS) 管理員**。 

2.  選擇電腦名稱，**網站**資料夾或您所設定的網站。  

3.  在功能表列上選擇 **動作** > **屬性**。  

4.  在 [ **HTTP 標頭**索引標籤上，選擇**MIME 類型**] 按鈕。  

5.  在  **MIME 類型** 視窗中，選擇**新增** 按鈕。  

6.  在 [ **MIME 類型**] 視窗中，輸入 **.vsto**作為延伸模組中，輸入**應用程式/x-ms-vsto**做為 MIME 輸入，然後再套用新設定。  

    > [!NOTE]  
    >  您必須重新啟動 World Wide Web Publishing 服務，或等待背景工作處理序回收，變更才會生效。 您必須接著清除瀏覽器的磁碟快取，並嘗試開啟 *.vsto*檔案一次。  

##### <a name="to-add-the-vsto-mime-type-to-iis-70"></a>若要將 .vsto MIME 類型加入至 IIS 7.0  

1.  在執行 IIS 7.0 伺服器上，選擇**開始** > **所有程式** > **附屬應用程式**。  

2.  開啟捷徑功能表**命令提示字元**，然後選擇 **系統管理員身分執行。**  

3.  在 [**開啟**方塊中，輸入下列路徑，然後選擇**確定**] 按鈕。  

    ```cmd
    %windir%\system32\inetsrv   
    ```  

4.  輸入下列命令，然後套用新的設定。  

    ```cmd
    set config /section:staticContent /+[fileExtension='.vsto',mimeType='application/x-ms-vsto']  
    ```  

    > [!NOTE]  
    >  您必須重新啟動 World Wide Web Publishing 服務，或是等待背景工作處理序回收，變更才會生效。 您必須接著清除瀏覽器的磁碟快取，並嘗試開啟 *.vsto*檔案一次。  

##  <a name="Put"></a> 將方案文件放置到終端使用者的電腦 （文件層級自訂）  
 您可以建立部署後動作，為其複製到使用者的電腦上將方案文件。 如此一來，使用者不需要他們的電腦從安裝位置手動複製文件之後安裝方案。 您必須建立定義部署後動作的類別、 建置及發行方案、 修改應用程式資訊清單，及重新簽署應用程式和部署資訊清單。  

 下列程序假設您的專案名稱**ExcelWorkbook**及您發行至方案**C:\publish**目錄在您的電腦上。  

### <a name="create-a-class-that-defines-the-post-deployment-action"></a>建立定義部署後動作的類別  

1. 在功能表列上選擇 **檔案** > **新增** > **新專案**。  

2. 在 **加入新的專案**對話方塊中，於**已安裝的範本**窗格中，選擇**Windows**資料夾。  

3. 在 **範本**窗格中，選擇**類別庫**範本。  

4. 在 **名稱**欄位中，輸入**FileCopyPDA**，然後選擇 **確定** 按鈕。  

5. 在 **方案總管**，選擇**FileCopyPDA**專案。  

6. 在功能表列上，選擇 [專案]  >  [加入參考]。  

7. 在  **.NET**索引標籤上，將參考加入至`Microsoft.VisualStudio.Tools.Applications.Runtime`和`Microsoft.VisualStudio.Tools.Applications.ServerDocument`。  

8. 將類別重新命名為 `FileCopyPDA`，然後將檔案的內容取代為程式碼。 這個程式碼會執行下列工作：  

   - 將文件複製到使用者的桌面。  

   - 變更的 _AssemblyLocation 屬性從相對路徑，為部署資訊清單的完整路徑。  

   - 如果使用者解除安裝方案，則將檔案刪除。  

     [!code-vb[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/VisualBasic/trin_excelworkbookpda/filecopypda/class1.vb#7)]
     [!code-csharp[Trin_ExcelWorkbookPDA#7](../vsto/codesnippet/CSharp/trin_excelworkbookpda/filecopypda/class1.cs#7)]  

### <a name="build-and-publish-the-solution"></a>建置及發行方案  

1.  在 [**方案總管] 中**，開啟捷徑功能表**FileCopyPDA**專案，，然後選擇**建置**。  

2.  開啟捷徑功能表**ExcelWorkbook**專案，，然後選擇**建置**。  

3.  開啟捷徑功能表**ExcelWorkbook**專案，，然後選擇**加入參考**。  

4.  中**加入參考**對話方塊方塊中，選擇**專案**索引標籤上，選擇 [ **FileCopyPDA**，然後選擇 **[確定]** ] 按鈕。  

5.  在 **方案總管**，選擇**ExcelWorkbook**專案。  

6.  在功能表列上選擇**專案** > **新資料夾**。  

7.  Enter**資料**，然後選擇**Enter**索引鍵。  

8.  在 **方案總管**，選擇**資料**資料夾。  

9. 在功能表列上選擇 **專案** > **加入現有項目**。  

10. 在 **加入現有項目** 對話方塊中，瀏覽至的輸出目錄**ExcelWorkbook**專案，選擇**ExcelWorkbook.xlsx**檔案，然後再選擇**新增** 按鈕。  

11. 在 **方案總管**選擇**ExcelWorkbook.xlsx**檔案。  

12. 在 **屬性**視窗中，變更**建置動作**屬性設**內容**和**複製到輸出目錄**屬性**有更新時才複製**。  

     當您完成這些步驟時，您的專案將會類似下圖。  

     ![部署後動作的專案結構。](../vsto/media/vsto-postdeployment.png "部署後動作的專案結構。")  

13. 發佈**ExcelWorkbook**專案。  

### <a name="modify-the-application-manifest"></a>修改應用程式資訊清單  

1.  開啟**c:\publish**使用目錄**檔案總管**。  

2.  開啟**應用程式檔案**資料夾，然後再開啟的資料夾對應至最新發行版本，您的方案。  

3.  開啟**ExcelWorkbook.dll.manifest**文字編輯器，例如 [記事本] 中的檔案。  

4.  在 `</vstav3:update>` 項目後面加上下列程式碼。 類別屬性`<vstav3:entryPoint>`項目，請使用下列語法： *NamespaceName.ClassName*。 在下列範例中，命名空間和類別名稱相同，因此產生的進入點名稱是 `FileCopyPDA.FileCopyPDA`。  

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

1.  在  **%USERPROFILE%\Documents\Visual Studio 2013\Projects\ExcelWorkbook\ExcelWorkbook**資料夾，複製**ExcelWorkbook_TemporaryKey.pfx**憑證檔案，並貼到*PublishFolder* **\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_資料夾。

2.  開啟 Visual Studio 命令提示字元中，然後將目錄變更為**c:\publish\Application Files\ExcelWorkbook**\__MostRecentPublishedVersion_資料夾 (例如**c:\publish\Application Files\ExcelWorkbook_1_0_0_4**)。  

3.  執行下列命令簽署修改後的應用程式資訊清單：  

    ```cmd
    mage -sign ExcelWorkbook.dll.manifest -certfile ExcelWorkbook_TemporaryKey.pfx  
    ```  

     「ExcelWorkbook.dll.manifest 簽署成功」訊息隨即顯示。  

4.  若要變更**c:\publish**資料夾，然後更新並簽署部署資訊清單執行下列命令：  

    ```cmd
    mage -update ExcelWorkbook.vsto -appmanifest "Application Files\Ex  
    celWorkbookMostRecentVersionNumber>\ExcelWorkbook.dll.manifest" -certfile "Application Files\ExcelWorkbookMostRecentVersionNumber>\ExcelWorkbook_TemporaryKey.pfx"  
    ```  

    > [!NOTE]  
    >  在上述範例中，將 MostRecentVersionNumber 您解決方案的最新的發行版本的版本號碼 (例如**1_0_0_4**)。  

     「ExcelWorkbook.vsto 簽署成功」訊息隨即顯示。  

5.  複製*ExcelWorkbook.vsto*的檔案**c:\publish\Application Files\ExcelWorkbook**\__MostRecentVersionNumber_目錄。  

##  <a name="SharePoint"></a> 將方案文件放置到執行 SharePoint （文件層級自訂） 的伺服器  
 您可以使用 SharePoint 將文件層級自訂發行至終端使用者。 當使用者前往 SharePoint 網站並開啟文件時，執行階段會自動將共用網路資料夾中的方案安裝到使用者的本機電腦。 方案安裝到本機上之後，即使文件是複製到其他地方 (例如桌面)，自訂仍舊會執行。  

#### <a name="to-put-the-document-on-a-server-thats-running-sharepoint"></a>若要將文件放置到執行 SharePoint 的伺服器上  

1.  將方案文件加入至 SharePoint 網站上的文件庫。  

2.  執行下列其中一種方法的步驟：  

    -   使用 Office 組態工具將執行 SharePoint 的伺服器加入至所有使用者電腦上 Word 或 Excel 中的 [信任中心]。  

         請參閱[安全性原則和設定 Office 2010 中的](http://go.microsoft.com/fwlink/?LinkId=99227)。  

    -   確定每位使用者都執行下列步驟。  

        1.  本機電腦上，開啟 Word 或 Excel 中，選擇**檔案**索引標籤，然後選擇**選項** 按鈕。  

        2.  在 [**信任中心**對話方塊方塊中，選擇**信任位置**] 按鈕。  

        3.  選取 [ **（不建議使用） 網路上允許之信任位置**核取方塊，然後再選擇**新增新的位置**] 按鈕。  

        4.  在 **路徑**方塊中，輸入包含您上傳的文件的 SharePoint 文件庫的 URL (例如*http://SharePointServerName/TeamName/ProjectName/DocumentLibraryName*)。  

             不將名稱加入預設的網頁，這類*default.aspx*或是*AllItems.aspx*。  

        5.  選取**也會信任此位置的子資料夾**核取方塊，然後再選擇**確定** 按鈕。  

             當使用者從 SharePoint 網站開啟文件時，文件隨即開啟，而且會安裝自訂。 使用者可以將文件複製到桌面。 自訂仍舊會執行，因為文件中的屬性是指向文件的網路位置。  

##  <a name="Custom"></a> 建立自訂安裝程式  
 您可以建立自訂安裝程式，您的 Office 解決方案，而不是使用發行方案時，會將為您建立的安裝程式。 例如，您可以使用登入指令檔開始進行安裝，或使用批次檔安裝方案而無須與使用者互動。 使用者電腦上已安裝必要條件時，下列情境可獲得最佳效果。  

 您的自訂安裝程序的一部分，呼叫 Office 方案的安裝程式工具 (*VSTOInstaller.exe*)，這預設會安裝在下列位置：  

 *%commonprogramfiles%\microsoft shared\VSTO\10.0\VSTOInstaller.exe*  

 如果此工具不在該位置中，您可以使用**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSTO Runtime Setup\v4\InstallerPath**或**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSTO Runtime Setup\v4\InstallerPath**登錄機碼來尋找該工具的路徑。  

 您可以使用以下參數*VSTOinstaller.exe*。  


| 參數 | 定義 |
|------------------| - |
| /Install 或 /I | 安裝方案。 這個選項後面必須接著部署資訊清單的路徑。 您可以指定本機電腦上的路徑，也就是通用命名慣例 (UNC) 檔案共用。 您可以指定本機路徑 (*C:\FolderName\PublishFolder*)，相對路徑 (*發佈\\*)，或完整限定的位置 (*\\\ServerName\FolderName*或 http://<em>ServerName/FolderName</em>)。 |
| /Uninstall 或 /U | 解除安裝方案。 這個選項後面必須接著部署資訊清單的路徑。 您可以指定位於本機電腦或 UNC 檔案共用上的路徑。 您可以指定本機路徑 (*c:\FolderName\PublishFolder*)，相對路徑 (*發佈\\*)，或完整限定的位置 (*\\\ServerName\FolderName*或 http://<em>ServerName/FolderName</em>)。 |
| /Silent 或 /S | 在不提示使用者輸入或顯示任何訊息的情況下，進行安裝或解除安裝。 如果需要信任提示，自訂不會安裝或更新。 |
| /Help 或 /? | 顯示 [說明] 資訊。 |

 當您執行*VSTOinstaller.exe*，可能會出現下列錯誤碼。  

|錯誤碼|定義|  
|----------------|----------------|  
|0|方案已成功安裝或解除安裝，或是出現 VSTOInstaller [說明]。|  
|-100|一個或多個命令列選項無效，或是設定超過一次。 如需詳細資訊，請輸入"vstoinstaller /？ 」 或參閱[建立自訂安裝 ClickOnce Office 方案](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)。|  
|-101|一或多個命令列選項無效。 如需詳細資訊，請輸入 "vstoinstaller /?"。|  
|-200|部署資訊清單 URI 無效。 如需詳細資訊，請輸入 "vstoinstaller /?"。|  
|-201|無法安裝方案，因為部署資訊清單無效。 請參閱[Deployment manifests for Office 方案](../vsto/deployment-manifests-for-office-solutions.md)。|  
|-202|Visual Studio Tools for Office 應用程式資訊清單區段無效，無法安裝方案。 請參閱[Application manifests for Office 方案](../vsto/application-manifests-for-office-solutions.md)。|  
|-203|無法安裝方案，因為發生下載錯誤。 請檢查部署資訊清單的 URI 或網路檔案的位置，然後再試一次。|  
|-300|無法安裝方案，因為發生安全性例外狀況。 請參閱[保護的 Office 方案](../vsto/securing-office-solutions.md)。|  
|-400|無法安裝方案。|  
|-401|無法解除安裝方案。|  
|-500|作業已取消，因為無法安裝或解除安裝方案，或是無法下載部署資訊清單。|  

##  <a name="Update"></a> 發行更新  
 若要更新的解決方案，它一次使用發行**專案設計工具**或是**發行精靈**，然後將更新的方案複製到安裝位置。 將檔案複製到安裝位置時，務必覆寫先前的檔案。  

 下一次方案檢查更新時，它會尋找並自動載入新的版本。  

##  <a name="Location"></a> 變更方案的安裝位置  
 您可以在發行方案之後，加入或變更安裝路徑。 基於下列其中一個或多個原因，您可能會想要變更安裝路徑：  

- 在知道安裝路徑之前就已編譯安裝程式。  

- 方案檔案已複製至不同位置。  

- 裝載安裝檔案的伺服器換了名稱或位置。  

  若要變更方案的安裝路徑，您必須更新安裝程式，然後使用者必須執行安裝程式。 若是文件層級自訂，使用者也必須更新其文件中的屬性，以指向新位置。  

> [!NOTE]  
>  如果您不想要求使用者更新其文件屬性，您可以要求使用者從安裝位置取得更新的文件。  

#### <a name="to-change-the-installation-path-in-the-setup-program"></a>若要變更安裝程式中的安裝路徑  

1. 開啟**命令提示字元**視窗，然後再將目錄變更至安裝資料夾。  

2. 執行安裝程式並且包含 `/url` 參數，這個參數會將新安裝路徑當成字串。  

    下列範例將示範如何將安裝路徑變更為 Fabrikam 網站上的位置，不過您可以將 URL 取代為您要的路徑：  

   ```cmd  
   setup.exe /url="http://www.fabrikam.com/newlocation"  
   ```  

   > [!NOTE]  
   >  如果出現訊息並指出可執行檔的簽章將失效，則用來簽署方案的憑證將不再有效且發行者為未知。 如此一來，使用者就必須確認可以信任方案的來源，才能進行安裝。  

   > [!NOTE]  
   >  若要顯示目前的 URL 值，請執行 `setup.exe /url`。  

   若是文件層級自訂，使用者必須開啟文件，然後更新其 _AssemblyLocation 屬性。 下列步驟將描述使用者如何執行這項工作。  

#### <a name="to-update-the-assemblylocation-property-in-a-document"></a>若要更新文件中的 _AssemblyLocation 屬性  

1.  在 **檔案**索引標籤上，選擇**資訊**下, 圖所示。  

     ![在 Excel 中的資訊 索引標籤](../vsto/media/vsto-infotab.png "在 Excel 中的資訊 索引標籤")  

2.  在 **屬性**清單中，選擇**進階屬性**下, 圖所示。  

     ![在 Excel 中的進階的屬性。](../vsto/media/vsto-advanceddocumentproperties.png "進階在 Excel 中的屬性。")  

3.  在 **自訂**索引標籤中**屬性**清單中，選擇 _AssemblyLocation，如下圖所示。  

     ![AssemblyLocation 屬性。](../vsto/media/vsto-assemblylocationproperty.png "AssemblyLocation 屬性。")  

     **值**方塊包含部署資訊清單識別碼。  

4.  識別項，前面輸入文件中，後面接著一條分隔線，格式的完整的路徑*路徑*|*識別碼*(比方說， *File://ServerName/FolderName/FileName | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9*。  

     如需如何格式化此識別項的詳細資訊，請參閱[自訂文件屬性概觀](../vsto/custom-document-properties-overview.md)。  

5.  選擇**確定**按鈕，然後儲存並關閉文件。  

6.  執行不含 /url 參數的安裝程式，在指定的位置安裝方案。  

##  <a name="Roll"></a> 將方案復原為舊版  
 當您復原方案時，可以將使用者還原為該方案的舊版。  

#### <a name="to-roll-back-a-solution"></a>若要復原方案  

1.  開啟方案的安裝位置。  

2.  在最上層發行資料夾中，刪除部署資訊清單 ( *.vsto*檔案)。  

3.  尋找要復原之版本的子資料夾。  

4.  將部署資訊清單從該資料夾複製至最上層發行資料夾。  

     例如，若要復原方案，稱為**OutlookAddIn1**從 1.0.0.1 1.0.0.0 版，將檔案複製**OutlookAddIn1.vsto**從**OutlookAddIn1_1_0_0_0**資料夾。 將檔案貼入最上層發行資料夾中，覆寫的版本專屬部署資訊清單**OutlookAddIn1_1_0_0_1** ，已經有。  

     下圖顯示這個範例中的發行資料夾結構。  

     ![發行資料夾結構](../vsto/media/publishfolderstructure.png "發行資料夾結構")  

     下次使用者開啟應用程式或自訂文件時，就會偵測到部署資訊清單的變更。 舊版 Office 方案便會從 ClickOnce 快取中執行。  

> [!NOTE]  
>  任何方案都只有前一個版本會儲存為本機資料。 如果復原兩個版本，則不會保留本機資料。 如需本機資料的詳細資訊，請參閱[存取 ClickOnce 應用程式中的本機和遠端資料](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications)。  

## <a name="see-also"></a>另請參閱  
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [發行 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [如何： 使用 ClickOnce 發行 Office 方案](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [如何： 安裝 ClickOnce Office 方案](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065)   
 [如何： 使用 ClickOnce 將文件層級 Office 方案發行到 SharePoint 伺服器](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)   
 [建立自訂安裝 ClickOnce office 方案](https://msdn.microsoft.com/3e5887ed-155f-485d-b8f6-3c02c074085e)  


