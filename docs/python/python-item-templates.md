---
title: Python 專案的項目範本
description: Python 專案項目範本的參考清單可在 Visual Studio 中透過 [加入] > [新項目] 對話方塊取得。
ms.date: 12/06/2018
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 23a79d0842592ff3ad68f63c2739a2af9847aaeb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945158"
---
# <a name="python-item-templates"></a>Python 項目範本

您可以透過 [**專案**  >  **加入新專案**] 功能表命令，在 Python 專案中取得專案範本，或在方案總管的內容功能表上使用 [**加入**  >  **新專案**] 命令。 

![[加入新項目] 對話方塊](media/project-item-templates.png)

使用您為項目提供的名稱時，範本通常會在專案中目前所選的資料夾內建立一或多個檔案和資料夾 (以滑鼠右鍵按一下資料夾可自動選取該資料夾的操作功能表)。 新增項目時，會將該項目包含在 Visual Studio 專案中，而且會出現的 [方案總管] 中。

下表簡短說明 Python 專案內每個項目範本的效果：

| 範本 | 範本建立的內容 |
| --- | --- |
| **空白 Python 檔案** | 副檔名為 *.py* 的空白檔案。 |
| **Python 類別** | 包含單一空白 Python 類別定義的 *.py* 檔案。 |
| **Python 套件** | 包含 *\_ \_ \_ \_ .py* 檔案的資料夾。 |
| **Python 單元測試** | 根據 `unittest` 架構進行一個單元測試的 *.py* 檔案，還有呼叫 `unittest.main()` 以執行檔案中的測試。 |
| **HTML 頁面** | 具有單一頁面結構的 *.html* 檔案，此結構包含 `<head>` 和 `<body>` 元素。 |
| **JavaScript** | 空白的 *.js* 檔案。 |
| **樣式表單** | 包含 `body` 的空白樣式的 *.css* 檔案。 |
| **文字檔** | 空白的 *.txt* 檔案。 |
| **Django 1.9 應用程式**<br/>**Django 1.4 應用程式** | 具有應用程式名稱的資料夾，其中包含如 Django 1.9 的[在 Visual Studio 中學習 Django，步驟 2-2](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) 中所說明的 Django 應用程式核心檔案。 針對 Django 1.4，不會包含 *migrations* 資料夾、*admin.py* 檔案與 *apps.py* 檔案。 |
| **IronPython WPF 視窗** | WPF 視窗包含兩個並存的檔案：使用空白的 `<Grid>` 元素定義 `<Window>` 的 *.xaml* 檔案，以及使用 `wpf` 程式庫來載入 XAML 檔案的相關聯 *.py* 檔案。 通常是在使用其中一個 IronPython 專案範本所建立的專案中使用。 請參閱[管理 Python 專案 - 專案範本](managing-python-projects-in-visual-studio.md#project-templates)。 |
| **Web 角色支援檔案** | 專案根目錄中的 *bin* 資料夾 (不論專案中所選的資料夾為何)。 該資料夾包含預設的部署指令碼和 Azure 雲端服務 Web 角色的 *web.config* 檔案。 該範本也包含說明詳細資料的 *readme.html* 檔案。 |
| **背景工作角色支援檔案** | 專案根目錄中的 *bin* 資料夾 (不論專案中所選的資料夾為何)。 該資料夾包含預設部署和啟動指令碼，還有 Azure 雲端服務背景工作角色的 *web.config* 檔案。 該範本也包含說明詳細資料的 *readme.html* 檔案。 |
| **Azure web.config (FastCGI)** | *web.config* 檔案，其中包含使用 [WSGI](https://wsgi.readthedocs.io/en/latest/) 物件來處理傳入連線之應用程式的項目。 此檔案通常會部署到執行 IIS 的網頁伺服器根目錄。 如需詳細資訊，請參閱[為應用程式設定 IIS](configure-web-apps-for-iis-windows.md)。 |
| **Azure web.config (HttpPlatformHandler)** | *web.config* 檔案，其中包含接聽傳入連線通訊端應用程式的項目。 此檔案通常部署在執行 IIS (例如 Azure App Service) 的 Web 伺服器根目錄。 如需詳細資訊，請參閱[為應用程式設定 IIS](configure-web-apps-for-iis-windows.md)。 |
| **Azure 靜態檔案 web.config** | 通常會新增到 *static* 資料夾 (或含有靜態項目的其他資料夾) 中以停用處理該資料夾之 Python 的 *web.config* 檔案。 此組態檔會與上述 FastCGI 或 HttpPlatformHandler 組態檔其中之一搭配運作。 如需詳細資訊，請參閱[為應用程式設定 IIS](configure-web-apps-for-iis-windows.md)。 |
| **Azure 遠端偵錯 web.config** | 已被取代 (用於在適用於 Windows 的 Azure App Service 上進行遠端偵錯，已不再支援)。 |

## <a name="see-also"></a>另請參閱

- [管理 Python 專案 - 專案範本](managing-python-projects-in-visual-studio.md#project-templates)
- [Python Web 專案範本](python-web-application-project-templates.md)
- [發佈至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)
