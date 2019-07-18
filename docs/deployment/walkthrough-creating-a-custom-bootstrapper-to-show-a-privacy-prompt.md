---
title: 逐步解說：建立具有隱私權提示的自訂啟動載入器 |Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00c5266d57ae5633313465796c718d989f783ea6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406854"
---
# <a name="walkthrough-create-a-custom-bootstrapper-with-a-privacy-prompt"></a>逐步解說：建立具有隱私權提示的自訂啟動載入器
您可以設定為自動更新時使用較新的檔案版本和組件版本的組件，就可以使用 ClickOnce 應用程式。 若要確定您的客戶同意加入這項行為，您可以顯示隱私權提示給他們。 然後，他們可以選擇是否要自動更新應用程式的權限授與。 如果應用程式不允許自動更新，它不會安裝。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

- Visual Studio 2010。

## <a name="create-an-update-consent-dialog-box"></a>建立更新同意對話方塊
 若要顯示隱私權提示，請建立應用程式詢問讀取器，同意應用程式的自動更新。

#### <a name="to-create-a-consent-dialog-box"></a>若要建立顯示同意對話方塊

1. 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。

2. 在 **新的專案** 對話方塊中，按一下**Windows**，然後按一下  **WindowsFormsApplication**。

3. 針對**名稱**，型別**ConsentDialog**，然後按一下**確定**。

4. 在設計師中，按一下 [表單]。

5. 在 **屬性**視窗中，變更**文字**屬性設**更新同意對話方塊**。

6. 中**工具箱**，展開**所有的 Windows Form**，然後將拖曳**標籤**控制項加入表單。

7. 在設計工具中，按一下 label 控制項。

8. 在 **屬性**視窗中，變更**文字**下的屬性**外觀**如下：

    您即將安裝的應用程式會檢查在網站上最新的更新。 藉由按一下 「 我同意 」，您可以授權檢查，並自動從網際網路安裝更新的應用程式。

9. 在 **工具箱**，拖曳**核取方塊**中間的表單控制項。

10. 在 **屬性**視窗中，變更**文字**下的屬性**版面配置**至**我同意**。

11. 在 [**工具箱**，拖曳 **] 按鈕**左下方的表單控制項。

12. 在 **屬性**視窗中，變更**文字**下的屬性**版面配置**至**繼續**。

13. 在 **屬性**視窗中，變更 **（名稱）** 下的屬性**設計**至**ProceedButton**。

14. 在 [**工具箱**，拖曳 **] 按鈕**右下方的表單控制項。

15. 在 **屬性**視窗中，變更**文字**下的屬性**版面配置**至**取消**。

16. 在 **屬性**視窗中，變更 **（名稱）** 下的屬性**設計**至**CancelButton**。

17. 在設計工具中，按兩下**我同意**核取方塊，以產生 CheckedChanged 事件處理常式。

18. 在 Form1 程式碼檔案中，新增下列程式碼 CheckedChanged 事件處理常式。

     [!code-csharp[ConsentDialog#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.cs)]
     [!code-vb[ConsentDialog#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_1.vb)]

19. 更新類別建構函式來停用**繼續**預設按鈕。

     [!code-csharp[ConsentDialog#6](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.cs)]
     [!code-vb[ConsentDialog#6](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_2.vb)]

20. 在 Form1 程式碼檔案中，新增布林值變數，來追蹤，如果使用者已經同意線上更新的下列程式碼。

     [!code-csharp[ConsentDialog#3](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.cs)]
     [!code-vb[ConsentDialog#3](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_3.vb)]

21. 在設計工具中，按兩下**繼續**按鈕，以產生 Click 事件處理常式。

22. 在 Form1 程式碼檔案中，將下列程式碼新增至 Click 事件處理常式，如**繼續** 按鈕。

     [!code-csharp[ConsentDialog#2](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.cs)]
     [!code-vb[ConsentDialog#2](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_4.vb)]

23. 在設計工具中，按兩下**取消**按鈕，以產生 Click 事件處理常式。

24. 在 Form1 程式碼檔案中，加入 [Click 事件處理常式，如下列程式碼**取消**] 按鈕。

     [!code-csharp[ConsentDialog#4](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.cs)]
     [!code-vb[ConsentDialog#4](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_5.vb)]

25. 傳回錯誤，如果使用者不同意線上更新應用程式更新。

     Visual Basic 開發人員只：

    1. 在 **方案總管**，按一下**ConsentDialog**。

    2. 在上**專案**功能表上，按一下**加入模組**，然後按一下 **新增**。

    3. 在  *Module1.vb*程式碼檔案，新增下列程式碼。

        [!code-vb[ConsentDialog#7](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_6.vb)]

    4. 在上**專案** 功能表中，按一下**ConsentDialog 屬性**，然後按一下**應用程式** 索引標籤。

    5. 取消核取**啟用應用程式架構**。

    6. 在 **啟始物件**下拉式選單中，選取**Module1**。

       > [!NOTE]
       > 停用的應用程式架構，會停用功能，例如 Windows XP 視覺化樣式、 應用程式事件、 啟動顯示畫面、 單一執行個體的應用程式等等。 如需詳細資訊，請參閱[專案設計工具、應用程式頁 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)。

       適用於 Visual C# 只有開發人員：

       開啟*Program.cs*程式碼檔案，並新增下列程式碼。

       [!code-csharp[ConsentDialog#5](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt_7.cs)]

26. 在 **建置**功能表上，按一下**和 BuildSolution**。

## <a name="create-the-custom-bootstrapper-package"></a>建立自訂啟動載入器套件
 若要顯示隱私權提示給使用者，您可以建立同意對話方塊中更新應用程式的自訂啟動載入器套件，並將它做為必要條件包含在所有 ClickOnce 應用程式。

 此程序示範如何藉由建立下列文件建立自訂啟動載入器套件：

- A *product.xml*資訊清單檔案，以描述啟動載入器的內容。

- A *package.xml*列出您的套件，例如字串和軟體授權條款的當地語系化特定層面的資訊清單檔案。

- 軟體授權條款的文件中。

#### <a name="step-1-to-create-the-bootstrapper-directory"></a>步驟 1：若要建立啟動載入器目錄

1. 建立名為**UpdateConsentDialog**中 *%PROGRAMFILES%\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*。

    > [!NOTE]
    > 您可能需要系統管理權限才能建立這個資料夾。

2. 在  *UpdateConsentDialog*目錄中，建立名為子目錄*en*。

    > [!NOTE]
    > 建立新的目錄，每個地區設定。 比方說，您可以新增 fr-fr，以 de 地區設定中的子目錄。 如有必要，這些目錄會包含法文與德文字串和語言套件。

#### <a name="step-2-to-create-the-productxml-manifest-file"></a>步驟 2：若要建立 product.xml 資訊清單檔

1. 建立文字檔案，稱為*product.xml*。

2. 在  *product.xml*檔案中，新增下列 XML 程式碼。 請確定您不覆寫現有的 XML 程式碼。

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

3. 將檔案儲存到 UpdateConsentDialog 啟動載入器目錄。

#### <a name="step-3-to-create-the-packagexml-manifest-file-and-the-software-license-terms"></a>步驟 3：若要建立 package.xml 資訊清單檔案和軟體授權條款

1. 建立文字檔案，稱為*package.xml*。

2. 在  *package.xml*檔案中，新增下列 XML 程式碼定義之地區設定，並包含的軟體授權條款。 請確定您不覆寫現有的 XML 程式碼。

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

3. 將檔案儲存在 UpdateConsentDialog 啟動載入器目錄的 en-us 子目錄。

4. 建立稱為 「 文件*eula.rtf*的軟體授權條款。

    > [!NOTE]
    > 軟體授權條款應該包含授權、 擔保、 責任和用戶所在地法律資訊。 這些檔案應該是地區設定特定，因此請確定該檔案會儲存在支援 MBCS 或 UNICODE 字元格式。 請參閱您的法務部門與內容相關的軟體授權條款。

5. 儲存文件中的 en-us 子目錄*UpdateConsentDialog*啟動載入器目錄。

6. 如有必要，建立新*package.xml*資訊清單檔案和新*eula.rtf*文件的每個地區設定的軟體授權條款。 比方說，如果您建立子目錄，fr，以 de 的地區設定，建立個別的 package.xml 資訊清單檔案和軟體授權條款，並將它們儲存到 fr，以 de 子目錄。

## <a name="set-the-update-consent-application-as-a-prerequisite"></a>將更新同意應用程式設定的必要元件
 在 Visual Studio 中，您可以設定更新同意應用程式的必要元件。

#### <a name="to-set-the-update-consent-application-as-a-prerequisite"></a>若要設定更新同意應用程式的必要元件

1. 在 [**方案總管] 中**，按一下您想要部署的應用程式的名稱。

2. 在 [專案] 功能表上，按一下 [ProjectName 屬性]。

3. 按一下 **發佈**頁面，然後再按一下**必要條件**。

4. 選取 **更新同意對話方塊**。

    > [!NOTE]
    > 您可能必須關閉再重新開啟 Visual Studio 以查看 必要條件 對話方塊中的 更新同意對話方塊。

5. 按一下 [確定] 。

## <a name="create-and-test-the-setup-program"></a>建立並測試安裝程式
 您將更新同意應用程式設定的必要元件之後，您可以產生應用程式的安裝程式並啟動載入器。

#### <a name="to-create-and-test-the-setup-program-by-not-clicking-i-agree"></a>建立及測試安裝程式未按一下 我同意

1. 在 [**方案總管] 中**，按一下您想要部署的應用程式的名稱。

2. 在 [專案] 功能表上，按一下 [ProjectName 屬性]。

3. 按一下 **發佈**頁面，然後再按一下**立即發佈**。

4. 如果發行輸出不會自動開啟，瀏覽至發行輸出。

5. 執行*Setup.exe*程式。

     安裝程式會顯示同意對話方塊中更新的軟體授權合約。

6. 閱讀軟體授權合約，然後按一下**接受**。

     同意對話方塊中更新應用程式隨即出現，並顯示下列文字：您即將安裝的應用程式會檢查在網站上最新的更新。 藉由按一下我同意，您會授權應用程式會自動在網際網路上的更新檢查。

7. 關閉應用程式，或按一下 [取消]。

     應用程式會顯示錯誤：安裝的系統元件時發生錯誤*ApplicationName*。 安裝程式無法繼續，直到成功安裝所有系統元件。

8. 按一下 詳細資料，以顯示下列錯誤訊息：元件更新同意對話方塊無法安裝並出現下列錯誤訊息：「 自動更新協議不是接受 」。 無法安裝下列元件:-更新同意對話方塊

9. 按一下 [ **關閉**]。

#### <a name="to-create-and-test-the-setup-program-by-clicking-i-agree"></a>建立及測試安裝程式按一下 我同意

1. 在 [**方案總管] 中**，按一下您想要部署的應用程式的名稱。

2. 在 [專案] 功能表上，按一下 [ProjectName 屬性]。

3. 按一下 **發佈**頁面，然後再按一下**立即發佈**。

4. 如果發行輸出不會自動開啟，瀏覽至發行輸出。

5. 執行*Setup.exe*程式。

     安裝程式會顯示同意對話方塊中更新的軟體授權合約。

6. 閱讀軟體授權合約，然後按一下**接受**。

     同意對話方塊中更新應用程式隨即出現，並顯示下列文字：您即將安裝的應用程式會檢查在網站上最新的更新。 藉由按一下我同意，您會授權應用程式會自動在網際網路上的更新檢查。

7. 按一下 **我同意**，然後按一下**繼續**。

     在應用程式開始安裝。

8. 如果出現 [安裝應用程式] 對話方塊中，按一下**安裝**。

## <a name="see-also"></a>另請參閱
- [應用程式部署必要條件](../deployment/application-deployment-prerequisites.md)
- [建立啟動載入器套件](../deployment/creating-bootstrapper-packages.md)
- [如何：建立產品資訊清單](../deployment/how-to-create-a-product-manifest.md)
- [如何：建立套件資訊清單](../deployment/how-to-create-a-package-manifest.md)
- [產品和套件結構描述參考](../deployment/product-and-package-schema-reference.md)