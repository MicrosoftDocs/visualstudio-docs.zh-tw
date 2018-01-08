---
title: "逐步解說： 建立舊版語言服務 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 660d33dd2d5c46d8020172c1fcf74bfb64b43360
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>逐步解說： 建立舊版語言服務
使用 managed 的封裝架構 (MPF) 語言類別實作中的語言服務[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]相當簡單。 您需要 VSPackage 也可以裝載語言服務、 語言服務本身，以及您的語言剖析器。  
  
## <a name="prerequisites"></a>必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../../extensibility/visual-studio-sdk.md)。  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio Package 專案範本位置  
 Visual Studio Package 專案範本位在三個不同的範本位置**新專案**對話方塊：  
  
1.  位在 Visual Basic 擴充性下。 專案的預設語言為 Visual Basic。  
  
2.  位在 C# 擴充性下。 專案的預設語言為 C#。  
  
3.  位在其他專案類型擴充性下。 專案的預設語言為 C++。  
  
### <a name="create-a-vspackage"></a>建立 VSPackage  
  
1.  Visual Studio Package 專案範本建立新的 VSPackage。  
  
     如果您要將語言服務加入現有的 VSPackage，略過下列步驟，並直接前往 「 建立語言服務類別 」 程序。  
  
2.  MyLanguagePackage 輸入專案的名稱，然後按一下**確定**。  
  
     您可以使用任何您想要的名稱。 這裡所詳述這些程序會假設 MyLanguagePackage 做為名稱。  
  
3.  選取[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]做為語言並產生新的金鑰檔案的選項。 按 [ **下一步**]。  
  
4.  輸入適當的公司和封裝資訊。 按 [ **下一步**]。  
  
5.  選取**功能表命令**。 按 [ **下一步**]。  
  
     如果您不想支援程式碼片段，您就可以按一下 [完成]，並略過下一個步驟。  
  
6.  輸入**插入程式碼片段**為**命令名稱**和`cmdidInsertSnippet`如**命令識別碼**。 按一下 [ **完成**]。  
  
     **命令名稱**和**命令 ID**可以是任何您想要的結果，這些是只是範例。  
  
### <a name="create-the-language-service-class"></a>建立語言服務類別  
  
1.  在**方案總管 中**，MyLanguagePackage 專案上按一下滑鼠右鍵，選擇**新增**，**參考**，然後選擇 **加入新參考**  按鈕。  
  
2.  在**加入參考**對話方塊中，選取**Microsoft.VisualStudio.Package.LanguageService**中**.NET**索引標籤上，按一下 **確定**。  
  
     這需要進行一次語言封裝專案。  
  
3.  在**方案總管 中**，以滑鼠右鍵按一下 VSPackage 專案，然後選取**新增**，**類別**。  
  
4.  請確定**類別**範本清單中選取。  
  
5.  輸入**MyLanguageService.cs**名稱的類別檔案，然後按一下**新增**。  
  
     您可以使用任何您想要的名稱。 這裡所詳述這些程序假設`MyLanguageService`做為名稱。  
  
6.  在 MyLanguageService.cs 檔案中，加入下列`using`陳述式。  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  修改`MyLanguageService`類別衍生自<xref:Microsoft.VisualStudio.Package.LanguageService>類別：  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  將游標的位置，從 「 LanguageService"與**編輯**， **IntelliSense**功能表上，選取**實作抽象類別**。 這會將所需的最小方法，實作語言服務類別。  
  
9. 實作抽象方法中所述[實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)。  
  
### <a name="register-the-language-service"></a>註冊語言服務  
  
1.  開啟 MyLanguagePackagePackage.cs 檔案並加入下列`using`陳述式：  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  註冊您的語言服務類別中所述[註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)。 這包括 「 Proffering 語言服務 」 各節與 ProvideXX 屬性。 使用本主題使用 TestLanguageService 位置 MyLanguageService。  
  
### <a name="the-parser-and-scanner"></a>剖析器和掃描器  
  
1.  實作中所述的剖析器和您語言的掃描器[舊版語言服務剖析器與掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)。  
  
     實作您的剖析器與掃描器的方式完全由您和已超出本主題的範圍。  
  
## <a name="language-service-features"></a>語言服務功能  
 語言服務實作每項功能，您通常衍生自適當的 MPF 語言服務類別的類別、 實作所有抽象方法，如有必要，並覆寫適當的方法。 您想要支援您建立及/或衍生自哪種類別是相依於的功能。 這些功能會在中詳細討論[舊版語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)。 下列程序是從 MPF 類別衍生類別的一般方法。  
  
#### <a name="deriving-from-an-mpf-class"></a>衍生自 MPF 類別  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下 VSPackage 專案，然後選取**新增**，**類別**。  
  
2.  請確定**類別**範本清單中選取。  
  
     輸入的類別檔案，一個適合的名稱，然後按一下**新增**。  
  
3.  在新的類別檔案，加入下列`using`陳述式。  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  修改類別來衍生自所需的 MPF 類別。  
  
5.  加入至少會採用相同的基底類別的建構函式參數的類別建構函式，並傳送至基底類別建構函式的建構函式參數。  
  
     例如，從衍生類別的建構函式<xref:Microsoft.VisualStudio.Package.Source>類別可能如下所示：  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  從**編輯**， **IntelliSense**功能表上，選取**實作抽象類別**如果基底類別必須實作所有抽象方法。  
  
7.  否則，將插入號類別內，並輸入要覆寫的方法。  
  
     例如，輸入`public override`若要查看所有方法都可以在該類別中覆寫清單。  
  
## <a name="see-also"></a>請參閱  
 [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)