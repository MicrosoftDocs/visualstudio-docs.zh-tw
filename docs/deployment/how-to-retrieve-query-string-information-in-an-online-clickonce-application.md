---
title: 在線上 ClickOnce 應用程式中取得查詢字串資訊
description: 瞭解 ClickOnce 應用程式如何讀取 URL 的查詢部分，以及如何使用 Mageui.exe 設定您的應用程式以接受查詢字串參數。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 49fd3ca9b625b9dec179ec37603e875cfdd296c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885127"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>How to: Retrieve query string information in an online ClickOnce application (如何：在線上 ClickOnce 應用程式中擷取查詢字串資訊)
*「查詢字串」* (query string) 是開頭為句號 (?) 之 URL 的部分，內含 *name=value* 格式的任意資訊。 假設您有裝載於 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 且名為 `WindowsApp1` 的 `servername`應用程式，而且想要在啟動應用程式時傳入變數 `username` 的值。 URL 可能如下所示：

 `http://servername/WindowsApp1.application?username=joeuser`

 下列兩個程序示範如何使用 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式來取得查詢字串資訊。

> [!NOTE]
> 如果正在使用 HTTP 啟動應用程式，而非使用檔案共用或本機檔案系統，則只能在查詢字串中傳遞資訊。

 第一個程序示範 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式如何在啟動應用程式時，使用一小部分的程式碼來讀取這些值。

 下一個程序示範如何使用 MageUI.exe 設定 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式，以接受查詢字串參數。 只要發行應用程式，就需要執行這項作業。

> [!NOTE]
> 當您決定啟用這項功能之前，請參閱本主題後面的＜安全性＞一節。

 如需有關如何 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 使用 *Mage.exe* 或 *MageUI.exe* 建立部署的詳細資訊，請參閱 [逐步解說：手動部署 ClickOnce 應用程式](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)。

> [!NOTE]
> 從 .NET Framework 3.5 SP1 開始，可以將命令列引數傳遞至離線 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。 如果您要提供應用程式的引數，則可以將參數傳入副檔名為 .APPREF-MS 的捷徑檔案。

### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>從 ClickOnce 應用程式取得查詢字串資訊

1. 請在專案中放入下列程式碼。 為了讓此程式碼能夠運作，您必須有 system.string 的參考，以及 `using` `Imports` 適用于 system.object、System.string 和 system.object 的 add 或指示詞。

     [!code-csharp[ClickOnceQueryString#1](../deployment/codesnippet/CSharp/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.cs)]
     [!code-vb[ClickOnceQueryString#1](../deployment/codesnippet/VisualBasic/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.vb)]

2. 呼叫先前定義的函式，以擷取依名稱編製索引之查詢字串參數的 <xref:System.Collections.DictionaryBase.Dictionary%2A> 。

### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>使用 MageUI.exe 將查詢字串傳入 ClickOnce 應用程式

1. 開啟 .NET 命令提示字元，並輸入：

   ```cmd
   MageUI
   ```

2. 從 [檔案]  功能表中，選取 [開啟] ，然後開啟您 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式的部署資訊清單，這是 `.application` 擴充功能中的檔案結尾。

3. 選取左導覽視窗中的 [部署選項]  面板，然後選取 [允許傳遞 URL 參數至應用程式]  核取方塊。

4. 從 [檔案]  功能表中，選取 [儲存] 。

> [!NOTE]
> 或者，您可以在 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]中啟用查詢字串傳遞。 選取 [允許傳遞 URL 參數至應用程式]  核取方塊，藉由開啟 [專案屬性] 、選取 [發行]  索引標籤、按一下 [選項]  按鈕，然後選取 [資訊清單] 即可找到此核取方塊。

## <a name="robust-programming"></a>穩固程式設計
 當您使用查詢字串參數時，必須仔細考慮要如何安裝和啟用應用程式。 如果您的應用程式設定成從 Web 或網路共用安裝在使用者的電腦上，則使用者可能只會透過 URL 啟用應用程式一次。 之後，使用者通常會使用 [開始]  功能表中的捷徑來啟用您的應用程式。 因此，保證您的應用程式只會在其存留期間接收到查詢字串引數一次。 如果您選擇將這些引數儲存在使用者的電腦上供日後使用，則必須負責以安全的方式儲存它們。

 如果您的應用程式只能在線上時使用，則一律會透過 URL 予以啟用。 不過，如果查詢字串參數遺失或損毀，則即使在此情況下，您的應用程式還是必須寫入才能正常運作。

## <a name="net-framework-security"></a>.NET Framework 安全性
 只有在使用之前想要清理任何惡意字元的輸入時，才允許將 URL 參數傳入 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 應用程式。 例如，如果在資料庫的 SQL 查詢中未進行篩選，則內嵌引號、斜線或分號的字串可能會執行任意資料作業。 如需查詢字串安全性的詳細資訊，請參閱 [腳本攻擊總覽](/previous-versions/w1sw53ds(v=vs.140))。

## <a name="see-also"></a>另請參閱
- [保護 ClickOnce 應用程式](../deployment/securing-clickonce-applications.md)