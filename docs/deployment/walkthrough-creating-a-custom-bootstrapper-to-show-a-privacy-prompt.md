---
title: "逐步解說：建立自訂啟動載入器以顯示隱私權提示 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce 部署, 必要條件"
  - "相依性 [.NET Framework], 自訂啟動載入器套件"
  - "部署應用程式 [Visual Studio], 自訂必要條件"
  - "必要條件 [.NET Framework], 自訂啟動載入器套件"
  - "Windows Installer 部署, 必要條件"
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# 逐步解說：建立自訂啟動載入器以顯示隱私權提示
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以將 ClickOnce 應用程式設定成在組件有更新版本的檔案和組件時自動更新。  為確認您的客戶同意此行為，您可以向他們顯示隱私權提示。  然後，他們可以選擇是否要授權讓應用程式自動更新。  如果不允許應用程式自動更新，則不會進行安裝。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   Visual Studio 2010。  
  
## 建立更新同意對話方塊  
 若要顯示隱私權提示，請建立要求讀者同意應用程式自動更新的應用程式。  
  
#### 若要建立同意對話方塊  
  
1.  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，按一下 \[**Windows**\]，然後按一下 \[**Windows Form 應用程式**\]。  
  
3.  在 \[**名稱**\] 中，輸入 ConsentDialog，然後按一下 \[**確定**\]。  
  
4.  在設計工具中按一下表單。  
  
5.  在 \[**屬性**\] 視窗中，將 \[**Text**\] 屬性變更為 Update Consent Dialog。  
  
6.  在 \[**工具箱**\] 中，展開 \[**所有 Windows Form**\]，並將 \[**Label**\] 控制項拖曳至表單中。  
  
7.  在設計工具中，按一下標籤控制項。  
  
8.  在 \[**屬性**\] 視窗中，將 \[**外觀**\] 下的 \[**Text**\] 屬性變更為下列文字：  
  
     您即將安裝的應用程式會在 Web 檢查是否有最新更新。  按一下 \[我同意\]，表示您授權應用程式從網際網路自動檢查並安裝更新。  
  
9. 在 \[**工具箱**\] 中，將 \[**Checkbox**\] 控制項拖曳至表單中央。  
  
10. 在 \[**屬性**\] 視窗中，將 \[**版面配置**\] 下的 \[**Text**\] 屬性變更為 \[我同意\]。  
  
11. 在 \[**工具箱**\] 中，將 \[**Button**\] 控制項拖曳至表單左下方。  
  
12. 在 \[**屬性**\] 視窗中，將 \[**版面配置**\] 下的 \[**Text**\] 屬性變更為 \[繼續\]。  
  
13. 在 \[**屬性**\] 視窗中，將 \[**設計**\] 下的 \[**\(名稱\)**\] 屬性變更為 ProceedButton。  
  
14. 在 \[**工具箱**\] 中，將 \[**Button**\] 控制項拖曳至表單右下方。  
  
15. 在 \[**屬性**\] 視窗中，將 \[**版面配置**\] 下的 \[**Text**\] 屬性變更為 \[取消\]。  
  
16. 在 \[**屬性**\] 視窗中，將 \[**設計**\] 下的 \[**\(名稱\)**\] 屬性變更為 CancelButton。  
  
17. 在設計工具中，按兩下 \[**我同意**\] 核取方塊，產生 CheckedChanged 事件處理常式。  
  
18. 在 Form1 程式碼檔案中，為 CheckedChanged 事件處理常式加入下列程式碼。  
  
     [!code-cs[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]  
  
19. 將類別建構函式更新成預設停用 \[**繼續**\] 按鈕。  
  
     [!code-cs[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]  
  
20. 在 Form1 程式碼檔案中，加入下列程式碼，讓布林值變數檢查使用者是否已經同意線上更新。  
  
     [!code-cs[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]  
  
21. 在設計工具中，按兩下 \[**繼續**\] 按鈕，產生 Click 事件處理常式。  
  
22. 在 Form1 程式碼檔案中，將下列程式碼加入至 \[**繼續**\] 按鈕的 Click 事件處理常式。  
  
     [!code-cs[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]  
  
23. 在設計工具中，按兩下 \[**取消**\] 按鈕，產生 Click 事件處理常式。  
  
24. 在 Form1 程式碼檔案中，為 \[**取消**\] 按鈕的 Click 事件處理常式加入下列程式碼。  
  
     [!code-cs[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]  
  
25. 將應用程式更新成在使用者不同意線上更新時傳回錯誤。  
  
     僅限 Visual Basic 開發人員：  
  
    1.  按一下 \[**方案總管**\] 中的 \[**ConsentDialog**\]。  
  
    2.  按一下 \[**專案**\] 功能表上的 \[**加入模組**\]，再按一下 \[**加入**\]。  
  
    3.  在 Module1.vb 程式碼檔案中，加入下列程式碼。  
  
         [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]  
  
    4.  在 \[**專案**\] 功能表上，按一下 \[**ConsentDialog 屬性**\]，然後按一下 \[**應用程式**\] 索引標籤。  
  
    5.  取消核取 \[**啟用應用程式架構**\]。  
  
    6.  選取 \[**啟始物件**\] 下拉式功能表中的 \[**Module1**\]。  
  
        > [!NOTE]
        >  停用應用程式架構會停用諸如 Windows XP 視覺化樣式、應用程式事件、啟動顯示畫面、單一執行個體應用程式等功能。  如需詳細資訊，請參閱 [應用程式頁面，專案設計工具 \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)。  
  
     僅限 Visual C\# 開發人員：  
  
     開啟 Program.cs 程式碼檔案並加入下列程式碼。  
  
     [!code-cs[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]  
  
26. 按一下 \[**建置**\] 功能表上的 \[**建置方案**\]。  
  
## 建立自訂啟動載入器套件  
 若要對使用者顯示隱私權提示，您可以建立 Update Consent Dialog 應用程式的自訂啟動載入器套件，並將它包含在所有 ClickOnce 應用程式中做為必要條件。  
  
 這個程序將示範如何透過建立下列文件來建立自訂啟動載入器套件：  
  
-   product.xml 資訊清單檔案，用以描述啟動載入器的內容。  
  
-   package.xml 資訊清單檔案，用以列出套件的當地語系化特定資訊，例如字串和軟體授權合約。  
  
-   軟體授權合約文件。  
  
#### 步驟 1：建立啟動載入器目錄  
  
1.  在 %PROGRAMFILES%\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages 目錄中，建立名為 UpdateConsentDialog 的目錄。  
  
    > [!NOTE]
    >  您需要有管理權限才能建立這個資料夾。  
  
2.  在 UpdateConsentDialog 目錄中，建立名為 en 的子目錄。  
  
    > [!NOTE]
    >  為每個地區設定建立新目錄。  例如，您可以加入 fr 和 de 地區設定的子目錄。  如有需要，這些目錄會包含法文和德文字串與語言套件。  
  
#### 步驟 2：建立 product.xml 資訊清單檔案  
  
1.  建立名為 `product.xml` 的文字檔。  
  
2.  在 product.xml 檔案中，加入下列 XML 程式碼。  請確認您並未覆寫現有的 XML 程式碼。  
  
    ```  
    <Product  
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      ProductCode="Microsoft.Sample.EULA">  
      <!-- Defines the list of files to be copied on build. -->  
      <PackageFiles CopyAllPackageFiles="false">  
        <PackageFile Name="ConsentDialog.exe"/>  
      </PackageFiles>  
  
      <!-- Defines how to run the Setup package.-->  
      <Commands >  
        <Command PackageFile = "ConsentDialog.exe" Arguments=''>  
          <ExitCodes>  
            <ExitCode Value="0" Result="Success" />  
            <ExitCode Value="-1" Result="Fail" String="AU_Unaccepted" />  
            <DefaultExitCode Result="Fail"   
              FormatMessageFromSystem="true" String="GeneralFailure" />  
          </ExitCodes>  
        </Command>  
      </Commands>  
  
    </Product>  
    ```  
  
3.  將檔案儲存至 UpdateConsentDialog 啟動載入器目錄。  
  
#### 步驟 3：建立 package.xml 資訊清單檔案和軟體授權合約  
  
1.  建立名為 `package.xml` 的文字檔。  
  
2.  在 package.xml 檔案中，加入下列 XML 程式碼，以定義地區設定並包含軟體授權合約。  請確認您並未覆寫現有的 XML 程式碼。  
  
    ```  
    <Package   
      xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
      Name="DisplayName"  
      Culture="Culture"  
      LicenseAgreement="eula.rtf">  
      <PackageFiles>  
        <PackageFile Name="eula.rtf"/>  
      </PackageFiles>  
  
      <!-- Defines a localizable string table for error messages. -->  
      <Strings>  
        <String Name="DisplayName">Update Consent Dialog</String>  
        <String Name="Culture">en</String>  
        <String Name="AU_Unaccepted">The automatic update agreement is not accepted.</String>  
        <String Name="GeneralFailure">A failure occurred attempting to launch the setup.</String>  
      </Strings>  
    </Package>  
    ```  
  
3.  將檔案儲存至 UpdateConsentDialog 啟動載入器目錄中的 en 子目錄。  
  
4.  為軟體授權合約文件建立名為 eula.rtf 的文件。  
  
    > [!NOTE]
    >  軟體授權合約應該包含授權、擔保、損害賠償責任和當地法律。  這些檔案應該是地區設定特定的，因此請確認檔案以支援 MBCS 或 UNICODE 字元的格式儲存。  關於軟體授權合約的內容，請洽詢您的法務部門。  
  
5.  將文件儲存至 UpdateConsentDialog 啟動載入器目錄中的 en 子目錄。  
  
6.  如有必要，為每個地區設定的授權合約建立新的 package.xml 資訊清單檔案和新的 eula.rtf 文件。  例如，如果您建立 fr 和 de 地區設定的子目錄，請分別建立 package.xml 資訊清單檔案和軟體授權合約並將它們儲存至 fr 和 de 子目錄。  
  
## 將 Update Consent 應用程式設定為必要條件  
 在 Visual Studio 中，您可以將 Update Consent 應用程式設定為必要條件。  
  
#### 若要將 Update Consent 應用程式設定為必要條件  
  
1.  在 \[**方案總管**\] 中，按一下您想要部署的應用程式名稱。  
  
2.  按一下 \[**專案**\] 功能表上的 \[*ProjectName* **屬性**\]。  
  
3.  按一下 \[**發行**\] 頁面，再按一下 \[**必要條件**\]。  
  
4.  選取 \[**Update Consent Dialog**\]。  
  
    > [!NOTE]
    >  您可能必須關閉並重新開啟 Visual Studio，才能在 \[必要條件對話方塊\] 中看到 \[Update Consent Dialog\]。  
  
5.  按一下 \[**確定**\]。  
  
## 建立並測試安裝程式  
 將 Update Consent 應用程式設定為必要條件之後，您可以產生應用程式的安裝程式和啟動載入器。  
  
#### 若要建立安裝程式，但不按一下我同意進行測試  
  
1.  在 \[**方案總管**\] 中，按一下您想要部署的應用程式名稱。  
  
2.  按一下 \[**專案**\] 功能表上的 \[*ProjectName* **屬性**\]。  
  
3.  按一下 \[**發行**\] 頁，然後按一下 \[**立即發行**\]。  
  
4.  如果發行輸出未自動開啟，請巡覽至發行輸出。  
  
5.  執行 Setup.exe 程式。  
  
     安裝程式隨即顯示 Update Consent Dialog 軟體授權合約。  
  
6.  閱讀軟體授權合約，然後按一下 \[**接受**\]。  
  
     Update Consent Dialog 應用程式隨即出現並顯示下列文字：您即將安裝的應用程式會在 Web 檢查是否有最新更新。  按一下 \[我同意\]，表示您授權應用程式從網際網路自動檢查並安裝更新。  
  
7.  關閉應用程式或按一下 \[取消\]。  
  
     應用程式隨即顯示錯誤：安裝 \<*應用程式名稱*\> 的系統元件時發生錯誤。  必須成功安裝所有系統元件，否則安裝程式無法繼續。  
  
8.  按一下 \[詳細資料\] 顯示下列錯誤訊息：無法安裝元件 Update Consent Dialog，並出現下列錯誤訊息: "The automatic update agreement is not accepted" \(使用者未接受自動更新授權合約\)。 無法安裝下列元件: \- Update Consent Dialog  
  
9. 按一下 \[**關閉**\]。  
  
#### 若要建立安裝程式，並按一下我同意進行測試  
  
1.  在 \[**方案總管**\] 中，按一下您想要部署的應用程式名稱。  
  
2.  按一下 \[**專案**\] 功能表上的 \[*ProjectName* **屬性**\]。  
  
3.  按一下 \[**發行**\] 頁，然後按一下 \[**立即發行**\]。  
  
4.  如果發行輸出未自動開啟，請巡覽至發行輸出。  
  
5.  執行 Setup.exe 程式。  
  
     安裝程式隨即顯示 Update Consent Dialog 軟體授權合約。  
  
6.  閱讀軟體授權合約，然後按一下 \[**接受**\]。  
  
     Update Consent Dialog 應用程式隨即出現並顯示下列文字：您即將安裝的應用程式會在 Web 檢查是否有最新更新。  按一下 \[我同意\]，表示您授權應用程式從網際網路自動檢查並安裝更新。  
  
7.  按一下 \[**我同意**\]，然後按一下 \[**繼續**\]。  
  
     應用程式隨即開始安裝。  
  
8.  如果出現 \[應用程式安裝\] 對話方塊，請按一下 \[**安裝**\]。  
  
## 請參閱  
 [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)   
 [建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)   
 [如何：建立產品資訊清單](../deployment/how-to-create-a-product-manifest.md)   
 [如何：建立封裝資訊清單](../deployment/how-to-create-a-package-manifest.md)   
 [產品和封裝結構描述參考](../deployment/product-and-package-schema-reference.md)