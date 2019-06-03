---
title: 自訂 SharePoint 方案套件，使用 MSBuild 目標
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71665f6ccf22ace264ff39831521538a335aed93
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401514"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>作法：使用 MSBuild 目標自訂 SharePoint 方案套件
  藉由在命令提示字元使用 MSBuild 目標，您可以自訂 Visual Studio 建立 SharePoint 封裝檔案的方式 ( *.wsp*)。 例如，您可以自訂變更封裝中繼目錄的 MSBuild 屬性，以及自訂指定列舉檔案的 MSBuild 項目群組。

## <a name="customize-and-run-msbuild-targets"></a>自訂及執行 MSBuild 目標
 如果您自訂 BeforeLayout 和 AfterLayout 目標，就可以在套件配置之前執行工作，例如加入、移除或修改將要封裝的檔案。

#### <a name="to-customize-the-beforelayout-target"></a>若要自訂 BeforeLayout 目標

1. 開啟編輯器 (例如 [記事本])，然後加入下列程式碼。

   ```xml
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Target Name="BeforeLayout">
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>
     </Target>
   </Project>
   ```

    這個範例會在封裝這個目標之前顯示訊息。

2. 將檔案命名**CustomLayout.SharePoint.targets**，然後將它儲存在 SharePoint 專案的資料夾。

3. 開啟專案，開啟其捷徑功能表，然後選擇**卸載專案**。

4. 在 **方案總管**，開啟專案的捷徑功能表，然後選擇**編輯** *\<專案名稱 >.vbproj*或**編輯** *\<專案名稱 >.csproj*。

5. 在專案檔結尾附近的 `Import` 這行後面，加入下列程式碼。

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. 儲存並關閉專案檔。

7. 在 **方案總管**，開啟專案的捷徑功能表，然後選擇**重新載入專案**。

   當您發行專案時，訊息會在封裝開始之前出現在輸出中。

#### <a name="to-customize-the-afterlayout-target"></a>若要自訂 AfterLayout 目標

1. 在功能表列上選擇 **檔案** > **Open** > **檔案**。

2. 在 **開啟的檔案** 對話方塊中，瀏覽至專案資料夾中，選擇 CustomLayout.target 檔案，，然後選擇**開啟** 按鈕。

3. 緊接在 `</Project>` 標記之前，加入下列程式碼：

   ```xml
   <Target Name="AfterLayout">
     <Message Importance="high" Text="In the AfterLayout Target"></Message>
   </Target>
   ```

    這個範例會在封裝這個目標之後顯示訊息。

4. 儲存並關閉目標檔案。

5. 重新啟動 Visual Studio，然後開啟專案。

   當您發行專案時，BeforeLayout 訊息會在封裝開始之前顯示，而 AfterLayout 訊息會在封裝完成之後顯示。

## <a name="see-also"></a>另請參閱
- [封裝和部署 SharePoint 方案](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
