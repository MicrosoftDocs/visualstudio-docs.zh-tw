---
title: 適用於 Python 的 Django Web 專案範本 | Microsoft Docs
description: 使用 Django 架構以 Python 所撰寫 Web 應用程式 Visual Studio 範本的概觀。
ms.custom: ''
ms.date: 07/13/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 941ec5191e440be95d66da983508de36cef6d4fd
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="django-web-project-template"></a>Django Web 專案範本

[Django (英文)](https://www.djangoproject.com/) 是高階的 Python 架構，專為快速、安全且可擴充的網頁程式開發所設計。 Visual Studio 中的 Python 支援可提供專案範本來設定 Django 架構 Web 應用程式的結構。 若要在 Visual Studio 中使用範本，請選取 [檔案] > [新增] > [專案]，並搜尋 "Django"，然後選取 [Django Web 專案]  範本。 產生的專案包含未定案程式碼，以及預設 SQLite 資料庫。 [Blank Django Web Project] (空白 Django Web 專案) 範本相似，但不包含資料庫。

Visual Studio 針對 Django 專案提供完整的 IntelliSense：

- 傳入範本的內容變數：

    ![內容變數的 IntelliSense](media/template-django-intellisense.png)

- 標記和篩選內建及使用者定義項目：

    ![標記和篩選的 IntelliSense](media/template-django-intellisense-filter.png)

- 內嵌 CSS 和 JavaScript 的語法著色：

    ![CSS IntelliSense](media/template-django-intellisense-css.png)

    ![JavaScript IntelliSense](media/template-django-intellisense-js.png)

Visual Studio 也針對 Django 專案提供完整的[偵錯支援](debugging-python-in-visual-studio.md)： 

![中斷點](media/template-django-debugging.png)

Django 專案一般是透過其 `manage.py` 檔案進行管理，而此檔案是 Visual Studio 所遵循的假設。 如果您停止使用該檔案作為進入點，則會中斷專案檔。 在該情況下，您需要[從現有檔案重新建立專案](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files)，而不要將它標示為 Django 專案。

## <a name="django-management-console"></a>Django 管理主控台

Django 管理主控台的存取方式是透過 [專案] 功能表上的各種命令，或是以滑鼠右鍵按一下方案總管中的專案。

- **開啟 Django 殼層**：在您的應用程式內容中開啟可讓您操作模型的殼層

    ![主控台](media/template-django-console-shell.png)

- **Django 同步 DB**︰在互動式的視窗中執行 `manage.py syncdb`：

    ![主控台](media/template-django-console-sync-db.png)

- **收集靜態**：執行 `manage.py collectstatic --noinput` 以將所有靜態檔案複製到由 `settings.py` 中的 `STATIC_ROOT` 所指定的路徑。 請注意，[發佈至 Microsoft Azure](python-web-application-project-templates.md#publishing-to-azure-app-service)時，發佈作業會自動收集靜態檔案。

    ![主控台](media/template-django-console-collect-static.png)

- **驗證**：執行 `manage.py validate`，這會報告由 `settings.py` 中的 `INSTALLED_APPS` 所指定之已安裝模組中的所有驗證錯誤：

    ![主控台](media/template-django-console-validate.png)