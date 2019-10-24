---
title: 逐步解說：建立舊版語言服務 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 694b1a53e72ca4e890e11befdc9b90f049e33dd1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721782"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>逐步解說：建立舊版語言服務
使用 managed package framework （MPF）語言類別，在 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 中執行語言服務相當簡單。 您需要 VSPackage 來裝載語言服務、語言服務本身，以及您語言的剖析器。

## <a name="prerequisites"></a>Prerequisites
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[VISUAL STUDIO SDK](../../extensibility/visual-studio-sdk.md)。

## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio Package 專案範本位置
 您可以在 [**新增專案**] 對話方塊的三個不同範本位置中找到 [Visual Studio 封裝] 專案範本：

1. 位在 Visual Basic 擴充性下。 專案的預設語言為 Visual Basic。

2. 位在 C# 擴充性下。 專案的預設語言為 C#。

3. 位在其他專案類型擴充性下。 專案的預設語言為 C++。

### <a name="create-a-vspackage"></a>建立 VSPackage

1. 使用 [Visual Studio 封裝] 專案範本建立新的 VSPackage。

    如果您要將語言服務新增至現有的 VSPackage，請略過下列步驟，並直接移至「建立語言服務類別」程式。

2. 輸入 MyLanguagePackage 作為專案的名稱，然後按一下 **[確定]** 。

    您可以使用任何您想要的名稱。 此處詳述的這些程式會假設 MyLanguagePackage 為名稱。

3. 選取 [[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]] 做為 [語言] 和 [選項]，以產生新的金鑰檔。 按 [ **下一步**]。

4. 輸入適當的公司和套件資訊。 按 [ **下一步**]。

5. 選取**功能表命令**。 按 [ **下一步**]。

    如果您不想要支援程式碼片段，可以直接按一下 [完成]，並略過下一個步驟。

6. 輸入 [**插入程式碼片段**] 做為**命令名稱**，並針對**命令識別碼**`cmdidInsertSnippet`。 按一下 [ **完成**]。

    **命令名稱**和**命令識別碼**可以是您想要的任何內容，這些只是範例。

### <a name="create-the-language-service-class"></a>建立語言服務類別

1. 在**方案總管**中，以滑鼠右鍵按一下 MyLanguagePackage 專案，選擇 [**加入**]、[**參考**]，然後選擇 [**加入新參考**] 按鈕。

2. 在 [**加入參考**] 對話方塊中，選取 [ **.net** ] 索引標籤中的 [ **VisualStudio LanguageService** ]，然後按一下 **[確定]** 。

     針對語言套件專案，這只需要執行一次。

3. 在**方案總管**中，以滑鼠右鍵按一下 VSPackage 專案，然後選取 [**新增**]、[**類別**]。

4. 請確定已在 [範本] 清單中選取 [**類別**]。

5. 輸入**MyLanguageService.cs**作為類別檔案名，然後按一下 [**新增**]。

     您可以使用任何您想要的名稱。 此處詳述的這些程式會假設 `MyLanguageService` 做為名稱。

6. 在 MyLanguageService.cs 檔案中，新增下列 `using` 指示詞。

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. 修改 `MyLanguageService` 類別，以衍生自 <xref:Microsoft.VisualStudio.Package.LanguageService> 類別：

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. 將游標放在 "LanguageService" 上，然後從 [**編輯**]、[ **IntelliSense** ] 功能表中選取 [**執行抽象類別**]。 這會新增必要的最低方法來執行語言服務類別。

9. 如[執行舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)中所述，執行抽象方法。

### <a name="register-the-language-service"></a>註冊語言服務

1. 開啟 MyLanguagePackagePackage.cs 檔案，並新增下列 `using` 指示詞：

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. 註冊語言服務類別，如[註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)中所述。 這包括 ProvideXX 屬性和「Proffering 語言服務」小節。 使用 MyLanguageService，本主題使用 TestLanguageService。

### <a name="the-parser-and-scanner"></a>剖析器和掃描器

1. 如[舊版語言服務剖析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)中所述，為您的語言執行剖析器和掃描器。

     您的剖析器和掃描器的執行方式完全取決於您，而且已超出本主題的範圍。

## <a name="language-service-features"></a>語言服務功能
 若要在語言服務中執行每項功能，您通常會從適當的 MPF 語言服務類別衍生類別，並視需要執行任何抽象方法，並覆寫適當的方法。 您建立及（或）衍生自哪些類別取決於您想要支援的功能。 [舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)中會詳細討論這些功能。 下列程式是從 MPF 類別衍生類別的一般方法。

#### <a name="deriving-from-an-mpf-class"></a>衍生自 MPF 類別

1. 在**方案總管**中，以滑鼠右鍵按一下 VSPackage 專案，然後選取 [**新增**]、[**類別**]。

2. 請確定已在 [範本] 清單中選取 [**類別**]。

     為類別檔案輸入適當的名稱，然後按一下 [**新增**]。

3. 在新的類別檔案中，新增下列 `using` 指示詞。

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. 修改類別，以從所需的 MPF 類別衍生。

5. 加入類別的函式，該函式會採用至少與基類的「檢查程式」相同的參數，並將的「處理常式」參數傳遞至基類的「函式」。

     例如，衍生自 <xref:Microsoft.VisualStudio.Package.Source> 類別的類別的函式可能如下所示：

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. 在 [**編輯**]、[ **IntelliSense** ] 功能表中，選取 [如果基類具有必須實作為的任何抽象方法，則**執行抽象類別**]。

7. 否則，請將插入號放在類別內，並輸入要覆寫的方法。

     例如，輸入 `public override` 以查看可以在該類別中覆寫之所有方法的清單。

## <a name="see-also"></a>請參閱
- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)
