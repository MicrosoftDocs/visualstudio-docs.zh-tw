---
title: 單元測試以舊版.NET Framework 為目標
description: 瞭解如何建立單元測試專案，以 .NET Framework 的特定版本為目標。 目標版本必須為 3.5 或更新版本，而且不能是用戶端版本。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 3f90a3d42eb1390adbb242242172aea152a0a54f
ms.sourcegitcommit: d526af3642163180e0cc3e1e73b0a00f02542683
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/31/2020
ms.locfileid: "97833230"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>如何：設定以舊版 .NET Framework 為目標的單元測試

當您在 Microsoft Visual Studio 中建立測試專案時，預設會將目標設為最新版本的 .NET Framework。 此外，如果您升級舊版的 Visual Studio 測試專案，它們也會升級成以最新版本的 .NET Framework 為目標。 藉由編輯專案屬性，您可以明確地將專案目標重定為舊版的 .NET Framework。

您可以建立以特定版本 .NET Framework 為目標的單元測試專案。 目標版本必須為 3.5 或更新版本，而且不能是用戶端版本。 Visual Studio 可針對以特定版本為目標的單元測試提供下列基本支援：

- 您可以建立單元測試專案，並將其目標設定為特定版本 .NET Framework。

- 您可以在本機電腦上的 Visual Studio 執行以特定版本 .NET Framework 為目標的單元測試。

- 您可以從命令提示字元使用 *MSTest.exe* ，來執行以特定 .NET Framework 版本為目標的單元測試。

- 您可以於建置過程中在組建代理程式上執行單元測試。

**測試 SharePoint 應用程式**

以上所列的功能同樣也能夠讓您使用 Visual Studio 撰寫 SharePoint 應用程式的單元測試和整合測試。 如需如何使用 Visual Studio 開發 SharePoint 應用程式的詳細資訊，請參閱[建立 SharePoint 方案](../sharepoint/create-sharepoint-solutions.md)、[建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)及[驗證及偵錯 SharePoint 程式碼](../sharepoint/verifying-and-debugging-sharepoint-code.md)。

**限制**

當您將測試專案目標重定為舊版 .NET Framework 時，將會套用以下限制：

- 在 .NET Framework 3.5 中，只有包含單元測試的測試專案才支援多目標。 .NET Framework 3.5 不支援任何其他測試類型，例如自動程式化 UI 或負載測試。 針對非單元測試的測試類型則會禁止重設目標。

- 只有在預設的主機介面卡中才支援執行以舊版 .NET Framework 為目標的測試。 ASP.NET 主機介面卡不支援執行這類測試。 必須在 ASP.NET 程式開發伺服器內容中執行的 ASP.NET 應用程式，必須與 .NET Framework 的目前版本相容。

- 當您執行支援 .NET Framework 3.5 多目標的測試時，會停用資料收集支援。 您可以使用 Visual Studio 命令列工具執行程式碼涵蓋範圍。

- 使用 .NET Framework 3.5 的單元測試無法在遠端電腦上執行。

- 您不能將單元測試的目標設定為架構的舊版用戶端版本。

## <a name="retargeting-for-visual-basic-unit-test-projects"></a>為 Visual Basic 單元測試專案重定目標

1. 建立新的 Visual Basic **單元測試專案** 專案。

2. 在 [方案總管] 中，從新的 Visual Basic 測試專案右鍵功能表選擇 [屬性]。

     隨即會顯示您的 Visual Basic 測試專案屬性。

3. 在 [ **編譯** ] 索引標籤上，選擇 [ **Advanced Compile 選項** ]，如下圖所示。

     ![進階編譯選項](../test/media/howtoconfigureunittest35frameworka.png)

4. 使用 [目標 Framework (所有組態)] 下拉式清單將目標架構變更為 [.NET Framework 3.5] 或是更新版本，如下圖的圖說文字 B 所示。 您不應指定用戶端版本。

     ![[Advanced 編譯器設定] 對話方塊的螢幕擷取畫面。 [目標 framework] 下拉式清單會反白顯示，並將值設定為 [.NET Frameowrk 3.5]。](../test/media/howtoconfigureunitest35frameworkstepb.png)

## <a name="retargeting-for-c-unit-test-projects"></a>為 C# 單元測試專案重定目標

1. 建立新的 c # **單元測試專案** 專案。

2. 在 [方案總管] 中，從新的 C# 測試專案右鍵功能表選擇 [屬性]。

   會隨即顯示您的 C# 測試專案屬性。

3. 在 [應用程式] 索引標籤上，選擇 [目標 Framework]。 從下拉式清單中，選擇 [.NET Framework 3.5] 或更新版本，如下圖所示。 您不應指定用戶端版本。

   ![[方案總管屬性] 窗格中的 [應用程式] 索引標籤的圖例，會反白顯示 [目標 framework] 下拉式清單的位置。](../test/media/howtoconfigureunittest35frameworkcsharp.png)

## <a name="retargeting-for-ccli-unit-test-projects"></a>為 C++/CLI 單元測試專案重定目標

1. 建立新的 C++ **單元測試專案** 專案。

   > [!WARNING]
   > 若要針對 Visual C++ 建置舊版 .NET Framework 的 C++/CLI 單元測試，您必須使用對應版本的 Visual Studio。

2. 在 [方案總管] 中，從新的 C++ 測試專案選擇 [卸載專案]。

3. 在 **方案總管** 中，選擇已卸載的 c + + 測試專案，然後選擇 [ **編輯 \<project name> .vcxproj**]。

   .Vcxproj 檔案會在編輯器中開啟 *。*

4. 將標籤為 `"Globals"` 的 `PropertyGroup` 中的 `TargetFrameworkVersion` 設定為版本 3.5 或更新版本。 您不應指定用戶端版本：

    ```xml
    <PropertyGroup Label="Globals">
        <TargetName>DefaultTest</TargetName>
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>
        <Keyword>ManagedCProj</Keyword>
        <RootNamespace>CPP_Test</RootNamespace>
      </PropertyGroup>
    ```

5. 儲存並關閉 *.vcxproj* 檔案。

6. 在 [方案總管] 中，從新的 C++ 測試專案右鍵功能表選取 [重新載入專案]。

## <a name="see-also"></a>請參閱

- [建立 SharePoint 方案](../sharepoint/create-sharepoint-solutions.md)
- [建置和偵錯 SharePoint 方案](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [[Advanced 編譯器設定] 對話方塊 (Visual Basic) ](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)
