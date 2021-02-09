---
title: 建立具有隱私權提示的自訂啟動載入器
description: 瞭解如何設定 ClickOnce 應用程式，以便在具有較新檔案版本和元件版本的元件可供使用時自動更新。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- dependencies [.NET Framework], custom bootstrapper package
- deploying applications [Visual Studio], custom prerequisites
- Windows Installer deployment, prerequisites
- prerequisites [.NET Framework], custom bootstrapper package
ms.assetid: 2f3edd6a-84d1-4864-a1ae-6a13c5732aae
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b2f36ee884beb3b79244e4621ba305c06aafe8ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915753"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>逐步解說：建立具有隱私權提示的自訂啟動載入器
您可以設定 ClickOnce 應用程式，以便在具有較新檔案版本和元件版本的元件可供使用時自動更新。 為確保您的客戶同意此行為，您可以向他們顯示隱私權提示。 然後，他們可以選擇是否要將許可權授與應用程式，以自動更新。 如果應用程式不允許自動更新，就不會安裝。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成這個逐步解說：

- Visual Studio 2010。

## <a name="create-an-update-consent-dialog-box"></a>[建立更新同意] 對話方塊
 若要顯示隱私提示，請建立應用程式，要求讀者同意應用程式的自動更新。

#### <a name="to-create-a-consent-dialog-box"></a>若要建立同意對話方塊

1. 在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。

2. 在 [ **新增專案** ] 對話方塊中，按一下 [ **視窗**]，然後按一下 [ **WindowsFormsApplication**]。

3. 在 [ **名稱**] 中，輸入 **ConsentDialog**，然後按一下 **[確定]**。

4. 在設計工具中，按一下表單。

5. 在 [ **屬性** ] 視窗中，將 [ **Text** ] 屬性變更為 [ **更新同意] 對話方塊**。

6. 在 [ **工具箱**] 中，展開 [ **所有 Windows Forms**]，並將 [ **標籤** ] 控制項拖曳至表單。

7. 在設計工具中，按一下 [標籤] 控制項。

8. 在 [**屬性**] 視窗中，將 [**外觀**] 下的 [**文字**] 屬性變更為下列內容：

    您即將安裝的應用程式會檢查網路上的最新更新。 按一下 [我同意] 即表示您已授權應用程式從網際網路自動檢查並安裝更新。

9. 在 [ **工具箱**] 中，將 **Checkbox** 控制項拖曳至表單的中間。

10. 在 [ **屬性** ] 視窗中，將 [配置] 底下的 [ **文字** ] 屬性 **變更為 [** **我同意**]

11. 在 [ **工具箱**] 中，將 **按鈕** 控制項拖曳至表單的左下方。

12. 在 [**屬性**] 視窗中，變更 [**版面** 配置] 下的 [ **Text** ] 屬性以 **繼續**。

13. 在 [**屬性**] 視窗中，將 [**設計**] **(名稱)** 屬性變更為 **ProceedButton**。

14. 在 [ **工具箱**] 中，將 **按鈕** 控制項拖曳至表單的右下角。

15. 在 [ **屬性** ] 視窗中，將 [配置] 底下的 [ **文字** ] 屬性 **變更為 [** **取消**]

16. 在 [**屬性**] 視窗中，將 [**設計**] **(名稱)** 屬性變更為 **CancelButton**。

17. 在設計工具中，按兩下 [ **我同意** ] 核取方塊以產生 CheckedChanged 事件處理常式。

18. 在 Form1 程式碼檔案中，加入 CheckedChanged 事件處理常式的下列程式碼。

     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]

19. 依預設，更新類別的函式以停用 [ **繼續** ] 按鈕。

     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]

20. 在 Form1 程式碼檔案中，為布林值變數新增下列程式碼，以追蹤終端使用者是否已同意線上更新。

     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]

21. 在設計工具中，按兩下 [ **繼續** ] 按鈕以產生 click 事件處理常式。

22. 在 Form1 程式碼檔案中，將下列程式碼加入至 [ **繼續** ] 按鈕的 Click 事件處理常式。

     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]

23. 在設計工具中，按兩下 [ **取消** ] 按鈕以產生 click 事件處理常式。

24. 在 Form1 程式碼檔案中，為 [ **取消** ] 按鈕的 Click 事件處理常式加入下列程式碼。

     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]

25. 更新應用程式，以在終端使用者不同意線上更新時傳回錯誤。

     僅限 Visual Basic 開發人員：

    1. 在 **方案總管** 中，按一下 [ **ConsentDialog**]。

    2. 在 [ **專案** ] 功能表上，按一下 [ **新增模組**]，然後按一下 [ **新增**]。

    3. 在 [ *Module1* ] 程式碼檔案中，加入下列程式碼。

        [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]

    4. 在 [ **專案** ] 功能表上，按一下 [ **ConsentDialog 屬性**]，然後按一下 [ **應用程式** ] 索引標籤。

    5. 取消核取 [ **啟用應用程式架構**]。

    6. 在 [ **啟始物件** ] 下拉式功能表中，選取 [ **Module1**]。

       > [!NOTE]
       > 停用應用程式架構會停用 Windows XP 視覺效果樣式、應用程式事件、啟動顯示畫面、單一實例應用程式等功能。 如需詳細資訊，請參閱 [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)。

       僅適用于 Visual c # 開發人員：

       開啟 *Program.cs* 程式碼檔案，然後加入下列程式碼。

       [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]

26. 在 [ **組建** ] 功能表上，按一下 [ **build.buildsolution**]。

## <a name="create-the-custom-bootstrapper-package"></a>建立自訂啟動載入器套件
 若要向使用者顯示隱私權提示，您可以為「更新同意」對話方塊應用程式建立自訂啟動載入器套件，並將它包含在所有 ClickOnce 應用程式中的先決條件。

 此程式示範如何藉由建立下列檔來建立自訂啟動載入器套件：

- 描述啟動載入器內容的 *product.xml* 資訊清單檔。

- *package.xml* 資訊清單檔，以列出套件的當地語系化特定層面，例如字串和軟體授權條款。

- 軟體授權條款的檔。

#### <a name="step-1-to-create-the-bootstrapper-directory"></a>步驟1：建立啟動載入器目錄

1. 在 *%PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* 中建立名為 **UpdateConsentDialog** 的目錄。

    > [!NOTE]
    > 您可能需要系統管理許可權才能建立此資料夾。

2. 在 *UpdateConsentDialog* 目錄中，建立名為 *en* 的子目錄。

    > [!NOTE]
    > 為每個地區設定建立新的目錄。 例如，您可以新增 fr 和 de 地區設定的子目錄。 如有必要，這些目錄會包含法文和德文字串和語言套件。

#### <a name="step-2-to-create-the-productxml-manifest-file"></a>步驟2：建立 product.xml 資訊清單檔

1. 建立稱為 *product.xml* 的文字檔。

2. 在 *product.xml* 檔案中，新增下列 XML 程式碼。 請確定您不會覆寫現有的 XML 程式碼。

    ```xml
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

3. 將檔案儲存至 UpdateConsentDialog 啟動載入器目錄。

#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>步驟3：建立 package.xml 的資訊清單檔和軟體授權條款

1. 建立稱為 *package.xml* 的文字檔。

2. 在 *package.xml* 檔案中，新增下列 XML 程式碼以定義地區設定，並包含軟體授權條款。 請確定您不會覆寫現有的 XML 程式碼。

    ```xml
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

3. 將檔案儲存到 UpdateConsentDialog 啟動載入器目錄中的 en 子目錄。

4. 為軟體授權條款建立稱為 *eula .rtf* 的檔。

    > [!NOTE]
    > 軟體授權條款應包含授權、擔保、債務和當地法律的相關資訊。 這些檔案應該是特定地區設定，因此請確定檔案的儲存格式可支援 MBCS 或 UNICODE 字元。 請洽詢您的法律部門，瞭解軟體授權條款的內容。

5. 將檔儲存至 *UpdateConsentDialog* 啟動載入器目錄中的 en 子目錄。

6. 如有必要，請建立新的 *package.xml* 資訊清單檔和新的 *eula .rtf* 檔，以取得每個地區設定的軟體授權條款。 例如，如果您建立了 fr 和 de 地區設定的子目錄，請建立個別 package.xml 的資訊清單檔案和軟體授權條款，並將其儲存至 fr 和 de 子目錄。

## <a name="set-the-update-consent-application-as-a-prerequisite"></a>將更新同意應用程式設定為必要條件
 在 Visual Studio 中，您可以將更新同意應用程式設定為必要條件。

#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>將更新同意應用程式設定為必要條件

1. 在 **方案總管** 中，按一下您想要部署的應用程式名稱。

2. 在 [專案] 功能表上，按一下[*ProjectName 屬性]* 。

3. 按一下 [ **發行** ] 頁面，然後按一下 [ **必要條件**]。

4. 選取 [ **更新同意] 對話方塊**。

    > [!NOTE]
    > 您可能必須關閉再重新開啟 Visual Studio，才能在 [必要條件] 對話方塊中查看 [更新同意] 對話方塊。

5. 按一下 [確定]  。

## <a name="create-and-test-the-setup-program"></a>建立並測試安裝程式
 將更新同意應用程式設定為必要條件之後，您可以為您的應用程式產生安裝程式和啟動載入器。

#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>若要建立並測試安裝程式，請不要按一下 [我同意]

1. 在 **方案總管** 中，按一下您想要部署的應用程式名稱。

2. 在 [專案] 功能表上，按一下[*ProjectName 屬性]* 。

3. 按一下 [ **發行** ] 頁面，然後按一下 [ **立即發佈**]。

4. 如果發行輸出未自動開啟，請流覽至發佈輸出。

5. 執行 *Setup.exe* 程式。

     安裝程式會顯示「更新同意」對話方塊軟體授權合約。

6. 閱讀軟體授權合約，然後按一下 [ **接受**]。

     更新同意對話方塊應用程式隨即出現，並顯示下列文字：您即將安裝的應用程式會檢查網路上是否有最新的更新。 按一下 [我同意] 即表示您已授權應用程式在網際網路上自動檢查更新。

7. 關閉應用程式，或按一下 [取消]。

     應用程式顯示錯誤：安裝 *ApplicationName* 的系統元件時發生錯誤。 安裝程式無法繼續，直到所有系統元件都安裝成功為止。

8. 按一下 [詳細資料] 以顯示下列錯誤訊息： [元件更新同意] 對話方塊安裝失敗，並出現下列錯誤訊息：「不接受自動更新合約」。 下列元件無法安裝：-更新同意對話方塊

9. 按一下 [關閉]  。

#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>若要建立並測試安裝程式，請按一下 [我同意]

1. 在 **方案總管** 中，按一下您想要部署的應用程式名稱。

2. 在 [專案] 功能表上，按一下[*ProjectName 屬性]* 。

3. 按一下 [ **發行** ] 頁面，然後按一下 [ **立即發佈**]。

4. 如果發行輸出未自動開啟，請流覽至發佈輸出。

5. 執行 *Setup.exe* 程式。

     安裝程式會顯示「更新同意」對話方塊軟體授權合約。

6. 閱讀軟體授權合約，然後按一下 [ **接受**]。

     更新同意對話方塊應用程式隨即出現，並顯示下列文字：您即將安裝的應用程式會檢查網路上是否有最新的更新。 按一下 [我同意] 即表示您已授權應用程式在網際網路上自動檢查更新。

7. 按一下 [ **我同意**]，然後按一下 [ **繼續**]。

     應用程式會開始安裝。

8. 如果出現 [應用程式安裝] 對話方塊，請按一下 [ **安裝**]。

## <a name="see-also"></a>另請參閱
- [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)
- [建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)
- [How to: Create a product manifest (如何：建立產品資訊清單)](../deployment/how-to-create-a-product-manifest.md)
- [How to: Create a package manifest (如何：建立封裝資訊清單)](../deployment/how-to-create-a-package-manifest.md)
- [產品和套件架構參考](../deployment/product-and-package-schema-reference.md)