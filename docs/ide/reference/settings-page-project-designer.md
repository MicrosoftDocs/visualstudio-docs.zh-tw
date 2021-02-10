---
title: 設定頁面、專案設計工具
description: 瞭解如何使用 [專案設計工具] 的 [設定] 頁面來指定專案的應用程式設定。
ms.custom: SEO-VS-2020
ms.date: 06/14/2018
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d8ee71e717d2287b4e6deb32b1b94c142cf7de73
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957669"
---
# <a name="settings-page-project-designer"></a>設定頁面、專案設計工具

使用 [專案設計工具] 的 [設定] 頁面來指定專案的應用程式設定。 應用程式設定讓您能動態地儲存和擷取應用程式的屬性設定和其他資訊。 它們也讓您能維護用戶端電腦上的自訂應用程式和使用者喜好設定。 如需詳細資訊，請參閱[管理應用程式設定](../managing-application-settings-dotnet.md)。

若要存取 [設定] 頁面，請選取 [方案總管] 中的專案節點，然後按一下 [專案] > [屬性]。 [專案設計工具] 出現時，請選取 [設定] 索引標籤。

## <a name="header-bar"></a>標頭列

在 [設定] 頁面頂端的標頭列包含數個控制項：

**同步處理**

[同步處理] 會將應用程式在執行階段或偵錯期間使用的使用者範圍設定還原成在設計階段定義的預設值。 若要還原資料，請從磁碟移除執行階段產生的應用程式特定檔案，而不是從專案資料移除。

**載入 Web 設定**

[載入 Web 設定] 會顯示 [登入] 對話方塊，讓您能載入已驗證使用者或匿名使用者的設定。 只有在您已在 [服務] 頁面上啟用用戶端應用程式服務，並指定 [Web 設定服務位置] 時，才會啟用此按鈕。

**檢視程式碼**

針對 C# 專案，[檢視程式碼] 按鈕讓您能檢視 *Settings.cs* 檔案中的程式碼。 這個檔案會定義 `Settings` 類別，它讓您能處理 `Settings` 物件上的特定事件。 在非 Visual Basic 的語言中，您必須明確呼叫此包裝函式類別的 `Save` 方法，才能保存使用者設定。 這通常在主要表單的 **Closing** 事件處理常式中執行。 以下是 `Save` 方法呼叫的範例：

```csharp
Properties.Settings.Default.Save();
```

針對 Visual Basic 專案，[檢視程式碼] 按鈕讓您能檢視 *Settings.vb* 檔案中的程式碼。 這個檔案會定義 `MySettings` 類別，它讓您能處理 `My.Settings` 物件上的特定事件。 如需使用 `My.Settings` 物件存取應用程式設定的詳細資訊，請參閱[存取應用程式設定](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)。

如需存取應用程式設定的詳細資訊，請參閱 [Windows Forms 的應用程式設定](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms)。

**存取修飾詞**

[存取修飾詞] 按鈕指定 `Properties.Settings` (在 C# 中) 或 `My.Settings`(在 Visual Basic 中) 協助程式類別的存取層級，Visual Studio 會在 *Settings.Designer.cs* 或 *Settings.Designer.vb* 中產生這些。

針對 Visual C# 專案，存取修飾詞可以是 **Internal** 或 **Public**。

針對 Visual Basic 專案，存取修飾詞可以是 **Friend** 或 **Public**。

根據預設，設定在 C# 是 **Internal**，在 Visual Basic 是 **Friend**。 當 Visual Studio 將協助程式類別產生為 **Internal** 或 **Friend** 時，可執行的 (*.exe*) 應用程式無法存取您已新增至類別庫 (*.dll* 檔案) 的資源和設定。 如果您必須共用來自類別庫的資源和設定，請將存取修飾詞設定為 **Public**。

如需設定協助程式類別的詳細資訊，請參閱[管理應用程式設定](../managing-application-settings-dotnet.md)。

## <a name="settings-grid"></a>設定方格

[設定方格] 用來設定應用程式設定。 此方格包含下列資料行：

**名稱**

輸入此欄位中應用程式設定的名稱。

**型別**

使用下拉式清單來選取設定類型。 最常使用的類型會出現在下拉式清單中，例如 **String**、**(Connection string)** 和 **System.Drawing.Font**。 您可以選取清單結尾的 [瀏覽]，然後從 [選取類型] 對話方塊選取類型，來選擇另一個類型。 選擇類型之後，會將它新增至下拉式清單中的常見類型 (僅適用於目前解決方案)。

**範圍**

選取 [應用程式] 或 [使用者]。

應用程式範圍的設定，例如連接字串，是與應用程式建立關聯。 使用者無法在執行階段變更應用程式範圍的設定。

使用者範圍的設定，例如系統字型，旨在用於使用者喜好設定。 使用者可以在執行階段變更這些。

**值**

與應用程式設定建立關聯的資料或值。 例如，如果設定為字型，其值可以是 **Verdana, 9.75pt, style=Bold**。

## <a name="see-also"></a>另請參閱

- [管理應用程式設定](../managing-application-settings-dotnet.md)
- [存取應用程式設定 (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
