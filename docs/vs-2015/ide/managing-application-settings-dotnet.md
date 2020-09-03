---
title: 管理應用程式設定 (.NET) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
ms.assetid: 35254321-ad14-47d9-b8c6-39ab3203c5d9
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85cc90170b2dc665bcdd5acd97860c47ef5a14c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "74293868"
---
# <a name="managing-application-settings-net"></a>管理應用程式設定 (.NET)

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

應用程式設定可讓您動態儲存應用程式資訊。 設定可以讓您在用戶端電腦上儲存不應包含在應用程式程式碼中的資訊 (例如連接字串)、使用者偏好設定和執行階段所需的其他資訊。

應用程式設定會取代舊版 Visual Studio 中使用的動態屬性。

每一個應用程式設定都必須具備唯一的名稱。 這個名稱可為字母、數字或底線的任意組合，但是不能以數字開頭，也不能包含空格。 透過 `Name` 屬性即可變更名稱。

應用程式設定可以儲存為任何資料類型，只要該類型可以序列化為 XML，或是具有可實作 `TypeConverter` / `ToString`/`FromString`。 最常見的類型是 `String`、 `Integer`和 `Boolean`，不過您也可以將值儲存為 <xref:System.Drawing.Color>、 <xref:System.Object>或連接字串。

應用程式設定也包含一個值。 該值是透過 **Value** 屬性來進行設定，而且必須符合設定的資料類型。

此外，應用程式設定也可在設計階段繫結到表單或控制項的屬性。

應用程式設定根據範圍可分成兩種類型：

- 應用程式範圍的設定可用於 Web 服務的 URL 或資料庫連接字串等資訊。 這些值與應用程式相關聯。 因此，使用者無法在執行時期變更。

- 使用者範圍的設定可用於保留表單最後一個位置或字型偏好設定等資訊。 使用者可以在執行階段變更這些值。

  您可以使用 [範圍] **** 屬性變更設定的類型。

  專案系統會將應用程式設定儲存在兩個 XML 檔案中：一個是您建立第一個應用程式設定時所建立的 app.config 檔案，另一個是在執行時期，當執行應用程式的使用者變更任何使用者設定的值時，所建立的 user.config 檔案。 請注意，使用者設定中的變更不會寫入磁碟中，除非應用程式明確呼叫方法以執行這個動作。

## <a name="creating-application-settings-at-design-time"></a>在設計階段建立應用程式設定

在設計階段建立應用程式設定有兩種方式：使用 [專案設計工具] **** 的 [設定] **** 頁面，或是使用表單或控制項的 [屬性] **** 視窗，這個視窗可讓您將設定繫結至屬性。

當您建立應用程式範圍的設定 (例如資料庫連接字串或伺服器資源參考) 時， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會將設定儲存在 app.config 中，並標示 `<applicationSettings>` 標記。 (連接字串儲存在 `<connectionStrings>` 標記之下)。

當您建立使用者範圍的設定 (例如預設字型、首頁或視窗大小) 時， [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會將設定儲存在 app.config 中的 `<userSettings>` 標記下。

> [!IMPORTANT]
> 當您將連接字串儲存在 app.config 中時，請特別謹慎，以免洩露連接字串中的重要資訊 (例如密碼或伺服器路徑)。
>
> 如果您是從外部來源取得連接字串資訊 (例如使用者提供使用者 ID 和密碼)，請務必確保您用來建構連接字串的值不能包含會變更連接行為的其他連接字串參數。
>
> 您可以考慮使用 [受保護的組態] 功能，將組態檔中的重要資訊加密。 如需詳細資訊，請參閱[保護連接資訊](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4)。

> [!NOTE]
> 由於類別庫 (Class Library) 沒有組態檔模型，因此應用程式設定不適用於類別庫專案。 但是 Visual Studio Tools for Office DLL 專案例外，它可以有組態檔。

## <a name="using-customized-settings-files"></a>使用自訂設定檔

您可以在專案中加入自訂設定檔，以便於管理設定群組。 單一檔案中所包含的設定會以單元方式載入和儲存。 因此，將設定儲存在經常使用及不常使用群組的個別檔案中，可以節省載入和儲存設定的時間。

例如，您可以將檔案 (如 SpecialSettings.settings) 加入至專案中。 雖然 `SpecialSettings` 類別不會出現在 `My` 命名空間中，但是 [檢視程式碼] **** 仍可讀取包含 `Partial Class SpecialSettings`的自訂設定檔。

設定設計工具會先搜尋專案系統所建立的設定檔案。這是 [ **設定** ] 索引標籤中的 [專案設計工具] 所顯示的預設檔案。設定。設定位於 [我的專案] 資料夾中的專案 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ，以及專案的 [屬性] 資料夾中 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 。 然後 [專案設計工具] 會搜尋專案的根資料夾中其他設定檔。 因此，您應該將自訂設定檔放在此。 如果您將 .settings 檔案加入至專案中的其他地方，[專案設計工具] 就無法找到檔案。

## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>於執行階段在 Visual Basic 中存取或變更應用程式設定

在 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 專案中，您可以使用 `My.Settings` 物件在執行階段存取應用程式設定。 請在 [設定]**** 頁面中，按一下 [檢視程式碼]**** 按鈕，以檢視 Settings.vb 檔案。 Settings.vb 會定義 `Settings` 類別，讓您用來處理設定類別上的下列事件： <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>、 <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>、 <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>和 <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>。 請注意，Settings.vb 中的 `Settings` 類別是部分類別，只會顯示使用者所擁有的程式碼，不會顯示整個產生的類別。 如需使用 `My.Settings` 物件存取應用程式設定的詳細資訊，請參閱 [Accessing Application Settings](https://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)。

使用者在執行階段所變更之任何使用者範圍的設定值 (例如表單的位置)，都會儲存在 user.config 檔案中。 請注意，預設值仍然是儲存在 app.config 中。

如果您在執行階段 (例如在測試應用程式時) 變更了任何使用者範圍的設定，想要將這些設定重設為預設值，請按一下 [同步處理] **** 按鈕。

強烈建議您使用 `My.Settings` 物件和預設的 .settings 檔來存取設定。 因為您可以使用 [設定設計工具] 將屬性指派給設定，並且會在應用程式關閉前自動儲存使用者設定。 然而， [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 應用程式可以直接存取設定。 在這個情況下，您必須存取 `MySettings` 類別，並且使用專案根目錄下的自訂 .settings 檔案。 您也必須在結束應用程式之前儲存使用者設定，如同您針對 C# 應用程式所做的一樣 (將於下一節中說明)。

<!-- markdownlint-disable MD003 MD020 -->
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-c"></a>在 Visual C# 中，於執行階段存取或變更應用程式設定
<!-- markdownlint-enable MD003 MD020 -->

在除了 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]之外的語言中 (例如 [!INCLUDE[csprcs](../includes/csprcs-md.md)])，您必須直接存取 `Settings` 類別，如下列 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 範例所示。

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

您也必須明確呼叫此包裝函式類別的 `Save` 方法，以保存使用者設定。 這通常在主要表單的 `Closing` 事件處理常式中執行。 下列 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 範例會示範呼叫 `Save` 方法。

```csharp
Properties.Settings.Default.Save();
```

如需透過 `Settings` 類別存取應用程式設定的一般資訊，請參閱 [Application Settings Overview](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)。 如需逐一查看設定的詳細資訊，請參閱此 [論壇文章](https://social.msdn.microsoft.com/Forums/en-US/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral)。

## <a name="see-also"></a>另請參閱

- [Accessing Application Settings](https://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)
