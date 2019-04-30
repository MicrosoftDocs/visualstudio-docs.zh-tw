---
title: HOW TO：在 Visual Studio 中建立 Office 專案
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e41b7714ce5f9a98e50092c1507457b848201773
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419606"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>HOW TO：在 Visual Studio 中建立 Office 專案
  您可以使用[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]建立 VSTO 增益集和文件層級自訂的 Microsoft Office 應用程式。 如需這些專案類型的詳細資訊，請參閱[Office 方案開發概觀&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-a-vsto-add-in-project"></a>建立 VSTO 增益集專案

1. 在 [檔案] 功能表上，選擇 [新增] > [專案]。 如果您的整合式的開發環境 (IDE) 設定為使用[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]開發設定，請在**檔案**功能表上，選擇 **新增** > **專案**。

    [ **新增專案** ] 對話方塊隨即出現。

   > [!NOTE]
   > Office 專案的目標預設為 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]。 如需詳細資訊，請參閱 < [.NET Framework client profile](/dotnet/framework/deployment/client-profile)。

2. 在 [範本] 窗格中，您要使用的語言節點下方展開**Office/SharePoint**。

3. 選擇**Office 增益集**節點。

4. 在專案範本清單中，選取 VSTO 增益集專案範本。 如需可用 VSTO 增益集專案範本的清單，請參閱 < [Office 專案範本概觀](../vsto/office-project-templates-overview.md)。

   > [!NOTE]
   > 如果專案範本不會顯示當您選取**Office 增益集**節點，請確定 **.NET Framework 4**或更新版本已在對話方塊頂端的下拉式方塊中選取。 Office 專案範本會顯示這兩個版本的 .NET Framework。

5. 在 **名稱**方塊中，輸入專案的名稱。 根據預設，專案名稱會與方案名稱相同。

6. 在 **位置**方塊中，輸入您想要用來建立專案的路徑。 您可以使用絕對路徑和通用命名慣例 (UNC) 路徑。 請勿使用 HTTP、FTP 或其他通訊協定的路徑。

    位置具有下列格式：

   * [*drive*\]\:

   * \\\\*Server*\\*Share*

     請勿在位置中使用下列字元：

   * 星號 (*)

   * 分隔號 (|)

   * 冒號 (:) (除非後接磁碟機代號)。

   * 雙引號 (") (包含空格的路徑不需要引號。)

   * 小於 (\<)

   * 大於 (>)

   * 問號 (?)

   * 百分比符號 (%)

7. 選擇 [確定]  按鈕。

   ::: moniker range="vs-2017"

   > [!NOTE]
   > 建立增益集專案時，一律會進行儲存， 而無法建立為暫存專案。 如需有關暫存專案的詳細資訊，請參閱[暫存專案](../ide/creating-solutions-and-projects.md#create-a-temporary-project)。

   ::: moniker-end

### <a name="to-create-a-document-level-customization-project"></a>若要建立文件層級的自訂專案

1. 在 [檔案] 功能表上，選擇 [新增] > [專案]。 如果您的 IDE 設定上使用 Visual Basic 開發設定，**檔案**功能表上，選擇**新增** > **專案**。

    [ **新增專案** ] 對話方塊隨即出現。

2. 在 [範本] 窗格中，您要使用的語言節點下方展開**Office/SharePoint**。

3. 選取 [Office 增益集]  節點。

4. 在專案範本清單中，選取文件層級的專案範本。 如需可用文件層級專案範本的清單，請參閱 < [Office 專案範本概觀](../vsto/office-project-templates-overview.md)。

   > [!NOTE]
   > 如果專案範本不會顯示當您選取**Office 增益集**節點，請確定 **.NET Framework 4**或更新版本已選取。

5. 在 **名稱**方塊中，輸入專案的名稱。 根據預設，此名稱也適用於文件。 如果您的 IDE 設定為使用 Visual C# 開發設定或一般開發設定，也請輸入位置和方案名稱。

   > [!NOTE]
   > 在專案位置的路徑或專案名稱中，您不能使用 Surrogate 字元。 此外，如果您打算將方案部署為供離線使用，則專案名稱中的字元必須符合 HTTP 通訊協定規格。

6. 選擇 [確定]  按鈕。

    隨即開啟 [Visual Studio Tools for Office 專案精靈]  。

7. 選取 **建立新的文件**如果您想要建立新的文件方案，或選取**複製現有文件**如果您想要自訂現有的文件。

    如果您建立新的文件時，指定中的名稱**名稱**方塊，然後使用選取的文件格式**格式** 方塊中。 如需可用格式的詳細資訊，請參閱[文件層級自訂的架構](../vsto/architecture-of-document-level-customizations.md)。

    如果您使用現有的文件時，指定的文件中的位置**現有的文件的完整路徑** 方塊中。 您可以使用絕對路徑和 UNC 路徑。 請勿使用 HTTP、FTP 或其他通訊協定的文件路徑。

    位置具有下列格式：

   - [*drive*\]\:

   - \\\\*Server*\\*Share*

     請勿在位置中使用下列字元：

   - 星號 (*)

   - 分隔號 (|)

   - 冒號 (:) (除非後接磁碟機代號)。

   - 雙引號 (") (包含空格的路徑不需要引號。)

   - 小於 (\<)

   - 大於 (>)

   - 問號 (?)

   - 百分比符號 (%)

   > [!NOTE]
   > 如果您要使用 [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 專案中的現有文件，則只能使用在 [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 中建立的文件，或必須轉換為此種文件才能使用。 同樣地，如果您要使用 Word 2010 專案中的現有文件，則只能使用在 Word 2010 中建立的文件，或必須轉換為此種文件才能使用。 如果您使用舊版 Word 中所建立的文件，文件中的特定功能將會停用。 如果您嘗試撰寫會用到這些功能的程式碼，專案可能會發生錯誤。 若要轉換的文件，請開啟該[!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]或 Word 2010 中，在**檔案**功能區上索引標籤中選擇**資訊** > **轉換**。

8. 選擇 [完成]。

9. 如有下列情況，請至 Word 的 [信任中心]，將專案資料夾及其子資料夾加入信任位置：

   - 您要建立 Word 文件為基礎 *.docm*檔案和文件包含 VBA 專案，或裝載 Windows Form 控制項。 將專案資料夾加入信任位置的清單，有助確保文件可以在設計階段如預期般運作。

   - 您要建立 Word 範本專案為基礎 *.dotx*檔案。 您必須將專案資料夾加入信任位置的清單，才能執行和偵錯專案。

     如需有關如何將文件新增至信任位置的詳細資訊，請參閱 Microsoft Office Online 網站[建立、 移除或變更檔案的信任位置](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)。

## <a name="see-also"></a>另請參閱
- [Office 專案範本概觀](../vsto/office-project-templates-overview.md)
- [Office 方案的共同開發](../vsto/collaborative-development-of-office-solutions.md)
- [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)
- [開始進行程式設計 VSTO 增益集](../vsto/getting-started-programming-vsto-add-ins.md)
