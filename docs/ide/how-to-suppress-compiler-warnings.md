---
title: 隱藏專案和 NuGet 套件的警告
description: 瞭解如何使用 Visual Studio 來篩選出一或多個編譯器警告類型，以清理組建記錄檔。
ms.custom: SEO-VS-2020
ms.date: 01/24/2018
ms.technology: vs-ide-compile
ms.topic: how-to
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab79521cfd4cc122fa398f88b56ca37e2f2673a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869176"
---
# <a name="how-to-suppress-compiler-warnings"></a>如何：隱藏編譯器警告

您可以簡化組建記錄檔，方法是篩選掉一或多個類型的編譯器警告。 例如，您可能只想檢閱當您將組建記錄檔詳細等級設定為 [一般]、[詳細資料] 或 [診斷] 時所產生的部分輸出。 如需詳細資訊的詳細資訊，請參閱 [如何：查看、儲存和設定組建記錄](../ide/how-to-view-save-and-configure-build-log-files.md)檔。

## <a name="suppress-specific-warnings-for-visual-c-or-f"></a>隱藏 Visual C# 或 F\# 的特定警告

使用 [組建] 屬性頁隱藏 C# 或 F# 專案的特定警告。

1. 在方案總管中，選擇您想要隱藏警告的專案。

1. 在功能表列上，選擇 [ **View**  >  **Property Pages**]。

1. 選擇 [組建] 頁面。

1. 在 [隱藏警告] 方塊中，指定您想要隱藏之警告的錯誤碼 (以分號分隔)。

1. 重建方案。

## <a name="suppress-specific-warnings-for-c"></a>隱藏 c + + 的特定警告

使用 [組態屬性] 屬性頁隱藏 C++ 專案的特定警告。

1. 在方案總管中，選擇您想要隱藏警告的專案或原始程式檔。

1. 在功能表列上，選擇 [ **View**  >  **Property Pages**]。

1. 選擇 [組態屬性] 分類，並選擇 [C/C++] 分類，然後選擇 [進階] 頁面。

1. 請執行下列其中一個步驟：

    - 在 [停用特定警告] 方塊中，指定您想要隱藏並以分號分隔之警告的錯誤碼。

    - 在 [停用特定警告] 方塊中，選擇 [編輯] 以顯示其他選項。

1. 選擇 [確定] 按鈕，然後重建方案。

## <a name="suppress-warnings-for-visual-basic"></a>隱藏 Visual Basic 的警告

編輯專案的 *.vbproj* 檔案，即可隱藏 Visual Basic 的特定編譯器警告。 若要依「類別」隱藏警告，您可以使用[編譯屬性頁](../ide/reference/compile-page-project-designer-visual-basic.md)。 如需詳細資訊，請參閱[在 Visual Basic 中設定警告](../ide/configuring-warnings-in-visual-basic.md)。

### <a name="to-suppress-specific-warnings-for-visual-basic"></a>隱藏 Visual Basic 的特定警告

此範例將示範如何編輯 *.vbproj* 檔案，以隱藏特定編譯器警告。

1. 在方案總管中，選擇您想要隱藏警告的專案。

1. 在功能表列上，選擇 [**專案** 卸載  >  **專案**]。

1. 在 **方案總管** 中，以滑鼠右鍵按一下開啟專案的捷徑功能表，然後選擇 [編輯 \<ProjectName>.vbproj]。

    隨即在程式碼編輯器中開啟 XML 專案檔。

1. 找出您正在建置之建置組態的 `<NoWarn>` 元素，並新增一或多個警告編號作為 `<NoWarn>` 元素的值。 如果您指定多個警告編號，則請以逗號予以分隔。

     下列範例示範 x86 平台上偵錯組建組態的 `<NoWarn>` 元素，並隱藏了兩個編譯器警告：

    ```xml
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

   > [!NOTE]
   > .NET Core 專案不包含預設的組建組態屬性群組。 若要隱藏.NET Core 專案中的警告，請手動將組建組態區段加入至檔案中。 例如：
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFramework>netcoreapp2.0</TargetFramework>
   >     <RootNamespace>VBDotNetCore_1</RootNamespace>
   >   </PropertyGroup>
   >   <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
   >     <NoWarn>42016,41999,42017</NoWarn>
   >   </PropertyGroup>
   > </Project>
   > ```

1. 將變更儲存至 *vbproj* 檔案。

1. 在功能表列上，選擇 [**專案**  >  **重載專案**]。

1. 在功能表列上，選擇 [**建立**  >  **重建方案**]。

    [輸出] 視窗不會再顯示您所指定的警告。

如需詳細資訊，請參閱 Visual Basic 命令列編譯器的 [/nowarn 編譯器選項](/dotnet/visual-basic/reference/command-line-compiler/nowarn)。

## <a name="suppress-warnings-for-nuget-packages"></a>隱藏 NuGet 套件的警告

在某些情況下，您可能想要隱藏單一 NuGet 套件的 NuGet 編譯器警告，而不是整個專案。 警告皆有其用途，因此不建議在專案層級隱藏它。 例如，其中一個 NuGet 警告會告訴您套件可能無法完全與您的專案相容。 如果您在專案層級隱藏警告，且隨後新增其他的 NuGet 套件，您將無法知道它是否已產生相容性警告。

### <a name="to-suppress-a-specific-warning-for-a-single-nuget-package"></a>隱藏單一 NuGet 套件的特定警告

1. 在 [方案總管] 中，選取您想要隱藏編譯器警告的 NuGet 套件。

   ![[方案總管] 中的 NuGet 套件](media/nuget-package-with-warning.png)

1. 從右鍵功能表或操作功能表中，選擇 [屬性]。

1. 在套件屬性的 [NoWarn] 方塊中，輸入您想要針對此套件隱藏的警告編號。 如果您想要隱藏多個警告，請使用逗號分隔警告數字。

   ![NuGet 套件屬性](media/nuget-properties-nowarn.png)

   警告會從 [方案總管] 和 [錯誤清單] 中消失。

## <a name="see-also"></a>另請參閱

- [逐步解說：建置應用程式](../ide/walkthrough-building-an-application.md)
- [如何：查看、儲存和設定組建記錄檔](../ide/how-to-view-save-and-configure-build-log-files.md)
- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
