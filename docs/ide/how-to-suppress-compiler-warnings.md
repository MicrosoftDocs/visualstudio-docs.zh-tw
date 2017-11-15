---
title: "如何：隱藏編譯器警告 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 77230702bf8dc582e176e4dd0f17eab3385966c6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-compiler-warnings"></a>如何：隱藏編譯器警告
您可以指定不想要組建記錄檔包含的一種或多種編譯器警告，來清理組建記錄檔。 例如，您可以使用這項技術，檢閱將組建記錄檔詳細資訊設定為 [一般]、[詳細] 或 [診斷] 時自動產生的一些資訊，而非所有資訊。 如需詳細資訊的詳細資訊，請參閱[如何：檢視、儲存和設定組建記錄檔](../ide/how-to-view-save-and-configure-build-log-files.md)。  
  
### <a name="to-suppress-specific-warnings-for-visual-c-or-f"></a>隱藏 Visual C# 或 F# 的特定警告 #
  
1.  在方案總管中，選擇您想要隱藏警告的專案。  
  
2.  在功能表列上選擇 [ **檢視**]、[ **屬性頁**]。  
  
3.  選擇 [組建] 頁面。  
  
4.  在 [隱藏警告] 方塊中，指定您想要隱藏並以分號分隔之警告的錯誤碼，然後重建方案。  
  
### <a name="to-suppress-specific-warnings-for-visual-c"></a>隱藏 Visual C++ 的特定警告  
  
1.  在方案總管中，選擇您想要隱藏警告的專案或原始程式檔。  
  
2.  在功能表列上選擇 [ **檢視**]、[ **屬性頁**]。  
  
3.  選擇 [組態屬性] 分類，並選擇 [C/C++] 分類，然後選擇 [進階] 頁面。  
  
4.  請執行下列其中一個步驟：  
  
    -   在 [停用特定警告] 方塊中，指定您想要隱藏並以分號分隔之警告的錯誤碼。  
  
    -   在 [停用特定警告] 方塊中，選擇 [編輯] 以顯示其他選項。  
  
5.  選擇 [確定] 按鈕，然後重建方案。  
  
## <a name="suppressing-warnings-for-visual-basic"></a>隱藏 Visual Basic 的警告  
 編輯專案的 .vbproj 檔案，即可隱藏 Visual basic 的特定編譯器警告。 您也可以使用[專案設計工具、編譯頁面](../ide/reference/compile-page-project-designer-visual-basic.md)，依分類來隱藏警告。 如需詳細資訊，請參閱[在 Visual Basic 中設定警告](../ide/configuring-warnings-in-visual-basic.md)。  
  
#### <a name="to-suppress-specific-warnings-for-visual-basic"></a>隱藏 Visual Basic 的特定警告  
  
1.  在方案總管中，選擇您想要隱藏警告的專案。  
  
2.  在功能表列上，依序選擇 [專案] 和 [卸載專案]。  
  
3.  在方案總管中，開啟專案的捷徑功能表，然後選擇 [編輯 *ProjectName***.vbproj**]。  
  
     該專案檔會在程式碼編輯器中開啟。  
  
4.  在用來建置的組建組態中，找到 `<NoWarn></NoWarn>` 項目。  
  
     下列範例示範粗體 `<NoWarn></NoWarn>` 項目代表 x86 平台上的偵錯組建組態︰  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn></NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  新增一個或多個警告編號作為 `<NoWarn>` 項目的值。 如果您指定多個警告編號，則請以逗號予以分隔，如下列範例所示。  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn>40059,42024</NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
6.  將變更儲存至 .vbproj 檔案。  
  
7.  在功能表列上，依序選擇 [專案] 和 [重新載入專案]。  
  
8.  在功能表列上，依序選擇 [建置] 和 [重建方案]。  
  
     [輸出] 視窗不會再顯示您所指定的警告。  
  
 如需詳細資訊，請參閱 [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：建置應用程式](../ide/walkthrough-building-an-application.md)   
 [如何：檢視、儲存和設定組建記錄檔](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
