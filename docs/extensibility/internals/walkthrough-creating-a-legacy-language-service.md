---
title: 演練:創建傳統語言服務 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59ec18ab0c97ec89422e06f5b33804adcc750d5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703692"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>逐步解說：建立舊版語言服務
使用託管包框架 (MPF) 語言類來實現[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]語言服務非常簡單。 您需要一個 VSPackage 來託管語言服務、語言服務本身以及語言的解析器。

## <a name="prerequisites"></a>Prerequisites
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 有關詳細資訊,請參閱[可視化工作室 SDK](../../extensibility/visual-studio-sdk.md)。

## <a name="locations-for-the-visual-studio-package-project-template"></a>Visual Studio Package 專案範本位置
 "可視化工作室包項目範本"可在 **"新專案"** 對話方塊中的三個不同範本位置找到:

1. 位在 Visual Basic 擴充性下。 專案的預設語言為 Visual Basic。

2. 位在 C# 擴充性下。 專案的預設語言為 C#。

3. 位在其他專案類型擴充性下。 專案的預設語言為 C++。

### <a name="create-a-vspackage"></a>建立 VS 套件

1. 使用可視化工作室包專案範本創建新的 VS 包。

    如果要將語言服務添加到現有 VSPackage,請跳過以下步驟,然後直接轉到"創建語言服務類"過程。

2. 輸入項目名稱的"我的語言包",然後單擊 **"確定**"。

    您可以使用任何所需的名稱。 此處詳述的這些過程將"我的語言包"作為名稱。

3. 選擇[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]作為語言和生成新密鑰檔的選項。 按 [下一步]  。

4. 輸入相應的公司和包裹資訊。 按 [下一步]  。

5. 選擇**選單指令**。 按 [下一步]  。

    如果您不打算支援代碼段,只需按一下"完成"並忽略下一步即可。

6. 輸入**的程式碼段**的指令**名稱**`cmdidInsertSnippet`與**指令代碼**。 按一下 [完成]  。

    **命令名稱**和**命令 ID**可以是所需的任何內容,這些只是示例。

### <a name="create-the-language-service-class"></a>建立語言服務類別

1. 在**解決方案資源管理員**中,右鍵單擊 My語言包項目,選擇 **「添加**」**參考**,然後選擇「**添加新參考」** 按鈕。

2. 在 **"新增參考"** 對話方塊中,在 **.NET**選項卡中選擇**Microsoft.VisualStudio.Package.語言服務**,然後按一下「**確定**」。

     對於語言包專案,只需執行一次此操作。

3. 在**解決方案資源管理員**中,右鍵按下 VSPackage 專案並選擇「**新增****」 類別**。

4. 使用樣本清單中選擇**了 類別**。

5. 輸入**類別檔名稱MyLanguage Service.cs,** 然後按下「**添加**」 。

     您可以使用任何所需的名稱。 此處詳述的這些過程`MyLanguageService`假定為名稱。

6. 在MyLanguage Service.cs檔中,添加`using`以下 指令。

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. 修改要`MyLanguageService`派生自類<xref:Microsoft.VisualStudio.Package.LanguageService>的 類別:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. 將游標放在"語言服務"和 **"編輯****、IntelliSense"** 選單中,選擇 **「實現抽象類**」。 這將添加實現語言服務類的最低必要方法。

9. 實現[實現舊語言服務](../../extensibility/internals/implementing-a-legacy-language-service2.md)中所述的抽象方法。

### <a name="register-the-language-service"></a>註冊語言服務

1. 開啟MyLanguagePackagePackage.cs檔並新增以下`using`指令:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. 註冊您的語言服務類,如[註冊舊語言服務](../../extensibility/internals/registering-a-legacy-language-service1.md)中所述。 這包括提供XX屬性和"提供語言服務" 部分。 使用"我的語言服務",本主題使用測試語言服務。

### <a name="the-parser-and-scanner"></a>解析器及掃描器

1. 實現您的語言的解析器和掃描器,如[舊語言服務解析器和掃描器](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)中所述。

     如何實現解析器和掃描器完全取決於您,並且超出了本主題的範圍。

## <a name="language-service-features"></a>語言服務功能
 要實現語言服務中的每個功能,通常從相應的 MPF 語言服務類派生一個類,根據需要實現任何抽象方法,並重寫適當的方法。 您創建和/或派生的類取決於要支援的功能。 這些功能在[舊語言服務功能](../../extensibility/internals/legacy-language-service-features1.md)中進行了詳細討論。 以下過程是從 MPF 類派生類的一般方法。

#### <a name="deriving-from-an-mpf-class"></a>從 MPF 類別派生

1. 在**解決方案資源管理員**中,右鍵按下 VSPackage 專案並選擇「**新增****」 類別**。

2. 使用樣本清單中選擇**了 類別**。

     輸入類檔的合適名稱,然後單擊 **「添加**」。。

3. 在新類檔中,添加以下`using`指令。

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. 修改類以從所需的 MPF 類派生。

5. 添加至少採用與基類構造函數相同的參數的類構造函數,並將構造函數參數傳遞給基類構造函數。

     例如,派生自類的<xref:Microsoft.VisualStudio.Package.Source>類的構造函數可能如下所示:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. 在 **「編輯****、IntelliSense」** 選單中,如果基類具有必須實現的任何抽象方法,請選擇 **「實現抽象類**」。

7. 否則,將 care 放置在類中,並輸入要重寫的方法。

     例如,鍵入`public override`以查看該類中可以重寫的所有方法的清單。

## <a name="see-also"></a>另請參閱
- [實作舊版語言服務](../../extensibility/internals/implementing-a-legacy-language-service1.md)
