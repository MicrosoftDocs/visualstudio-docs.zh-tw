---
title: 管理應用程式設定 (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d792a6147795f81211203fc442539371f3caa91
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593703"
---
# <a name="manage-application-settings-net"></a>管理應用程式設定 (.NET)

應用程式設定可讓您動態儲存應用程式資訊。 設置允許您在用戶端電腦上存儲不應包含在應用程式代碼中的資訊（例如連接字串）、使用者首選項以及運行時所需的其他資訊。

應用程式設定會取代舊版 Visual Studio 中使用的動態屬性。

每一個應用程式設定都必須具備唯一的名稱。 這個名稱可為字母、數字或底線的任意組合，但是不能以數字開頭，也不能有空格。 透過 `Name` 屬性即可變更名稱。

應用程式設定可以儲存為任何資料類型，只要該類型會序列化為 XML，或是具有可實作 `ToString`/`FromString` 的 `TypeConverter`。 最常見的類型是 `String`、 `Integer`和 `Boolean`，不過您也可以將值儲存為 <xref:System.Drawing.Color>、 <xref:System.Object>或連接字串。

應用程式設定也有一個值。 該值是透過 **Value** 屬性來進行設定，而且必須符合設定的資料類型。

此外，應用程式設定也可在設計階段繫結到表單或控制項的屬性。

應用程式設定根據範圍可分成兩種類型：

- 應用程式範圍的設定可用於 Web 服務的 URL 或資料庫連接字串等資訊。 這些值與應用程式相關聯。 因此，使用者無法在執行時期變更。

- 使用者範圍的設定可用於保留表單最後一個位置或字型偏好設定等資訊。 使用者可以在執行階段變更這些值。

您可以使用 [範圍] **** 屬性變更設定的類型。

專案系統會將應用程式設定儲存在兩個 XML 檔案中：

- *app.config*檔，該檔在創建第一個應用程式設定時在設計時創建

- *user.config*檔，該檔是在運行時運行應用程式的使用者更改任何使用者設置的值時創建的。

請注意，使用者設定中的變更不會寫入磁碟中，除非應用程式明確呼叫方法以執行這個動作。

## <a name="create-application-settings-at-design-time"></a>在設計階段建立應用程式設定

在設計階段建立應用程式設定有兩種方式：使用 [專案設計工具] **** 的 [設定] **** 頁面，或是使用表單或控制項的 [屬性] **** 視窗，這個視窗可讓您將設定繫結至屬性。

創建應用程式範圍設置（例如，資料庫連接字串或對伺服器資源的引用）時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]請將其保存在*app.config*中。 `<applicationSettings>` (連接字串儲存在 `<connectionStrings>` 標記之下)。

創建使用者範圍設置（例如，預設字型、主頁或視窗大小）時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]請將其保存在*app.config*中，並帶有`<userSettings>`標記。

> [!IMPORTANT]
> 在*app.config 中*存儲連接字串時，應採取預防措施，避免在連接字串中顯示敏感資訊（如密碼或伺服器路徑）。
>
> 如果您是從外部來源取得連接字串資訊 (例如使用者提供使用者 ID 和密碼)，請務必確保您用來建構連接字串的值不能包含會變更連接行為的其他連接字串參數。
>
> 您可以考慮使用 [受保護的組態] 功能，將組態檔中的重要資訊加密。 如需詳細資訊，請參閱[保護連線資訊](/dotnet/framework/data/adonet/protecting-connection-information)。

> [!NOTE]
> 由於類別庫 (Class Library) 沒有組態檔模型，因此應用程式設定不適用於類別庫專案。 但是 Visual Studio Tools for Office DLL 專案例外，它可以有組態檔。

## <a name="use-customized-settings-files"></a>使用自訂的設定檔

您可以在專案中加入自訂設定檔，以便於管理設定群組。 單一檔案中所包含的設定會以單元方式載入和儲存。 將設定儲存在經常使用及不常使用群組的個別檔案中，可以節省載入和儲存設定的時間。

例如，您可以將檔（如*特殊設置.設置*）添加到專案中。 雖然 `SpecialSettings` 類別不會出現在 `My` 命名空間中，但是 [檢視程式碼] **** 仍可讀取包含 `Partial Class SpecialSettings`的自訂設定檔。

**設置設計器**首先搜索專案系統創建的 *"設置設置"* 檔;此檔是**專案設計器**在 **"設置"** 選項卡中顯示的預設檔 *。"設置.設置"* 位於[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]專案的"*我的專案"* 資料夾中以及[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]專案*的屬性*資料夾中。 然後，**專案設計器**在專案的根資料夾中搜索其他設置檔。 因此，您應該將自訂設定檔放在此。 如果在專案的其他位置添加 *.設置*檔，**則專案設計器**將無法找到它。

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>在 Visual Basic 中於執行階段存取或變更應用程式設定

在 Visual Basic 專案中，您可以使用 `My.Settings` 物件在執行階段存取應用程式設定。 請在 [設定]**** 頁面中，按一下 [檢視程式碼]**** 按鈕，以檢視 *Settings.vb* 檔案。 *Settings.vb*`Settings`定義類，這使您能夠在設置類上處理這些事件<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>： 、<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged><xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>和<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>。 請注意，*Settings.vb* 中的 `Settings` 類別是部分類別，只會顯示使用者所擁有的程式碼，不會顯示整個產生的類別。 如需使用 `My.Settings` 物件存取應用程式設定的詳細資訊，請參閱[存取應用程式設定 (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)。

使用者在運行時更改的任何使用者範圍設置的值（例如，表單的位置）都存儲在*user.config*檔中。 請注意，預設值仍保存在*app.config*中。

如果在執行階段期間 (例如在測試應用程式時) 變更了任何使用者範圍的設定，並想要將這些設定重設為預設值，請按一下 [同步處理]**** 按鈕。

我們強烈建議您使用`My.Settings`物件和預設 *.設置*檔來訪問設置。 這是因為您可以使用 **"設置設計器"** 為設置分配屬性，此外，使用者設置在應用程式關閉之前會自動儲存。 然而，Visual Basic 應用程式可以直接存取設定。 在這種情況下，您必須訪問類`MySettings`並使用專案根目錄中的自訂 *.settings*檔。 您必須在結束應用程式之前儲存使用者設定，如同您針對 C# 應用程式所做的一樣 (將於下一節中描述)。

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>在 C# 中於執行階段存取或變更應用程式設定
<!-- markdownlint-enable MD003 MD020 -->

在除了 Visual Basic 之外的語言中 (例如 C#)，您必須直接存取 `Settings` 類別，如下列 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 範例所示。

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

您必須明確呼叫此包裝函式類別的 `Save` 方法，才能保存使用者設定。 這通常在主要表單的 `Closing` 事件處理常式中執行。 下列 C# 範例會示範呼叫 `Save` 方法。

```csharp
Properties.Settings.Default.Save();
```

如需透過 `Settings` 類別存取應用程式設定的一般資訊，請參閱[應用程式設定概觀 (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview)。 如需逐一查看設定的詳細資訊，請參閱此 [論壇文章](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral)。

## <a name="see-also"></a>另請參閱

- [存取應用程式設定 (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
