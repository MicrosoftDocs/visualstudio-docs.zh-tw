---
title: 適用於 Python 的 Django Web 專案範本
description: 使用 Django 架構以 Python 所撰寫 Web 應用程式 Visual Studio 範本的概觀。
ms.date: 07/03/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: e847322b1bbbefec5c7013d7e90475e08f42694b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499539"
---
# <a name="django-web-project-template"></a>Django Web 專案範本

[Django (英文)](https://www.djangoproject.com/) 是高階的 Python 架構，專為快速、安全且可擴充的網頁程式開發所設計。 Visual Studio 中的 Python 支援提供數個專案範本，可設定以 Django 為基礎的 Web 應用程式結構。 若要在 Visual Studio 中使用範本，請選取 [檔案] > [新增] > [專案]，搜尋 "Django"，然後從 [空白 Django Web 專案]、[Django Web 專案] 和 [投票 Django Web 專案] 範本中選取。 如需所有範本的逐步解說，請參閱[學習 Django 教學課程](learn-django-in-visual-studio-step-01-project-and-solution.md)。

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

Django 專案一般是透過其 *manage.py* 檔案進行管理，而此檔案是 Visual Studio 所遵循的假設。 如果您停止使用該檔案作為進入點，則會中斷專案檔。 在該情況下，您需要[從現有檔案重新建立專案](managing-python-projects-in-visual-studio.md#create-a-project-from-existing-files)，而不要將它標示為 Django 專案。

## <a name="django-management-console"></a>Django 管理主控台

Django 管理主控台的存取方式是透過 [專案] 功能表上的各種命令，或是以滑鼠右鍵按一下 [方案總管] 中的專案。

- **開啟 Django 殼層**：在您的應用程式內容中開啟可讓您操作模型的殼層：

    ![主控台](media/template-django-console-shell.png)

- **Django 同步 DB**：在**互動式** 視窗中執行 `manage.py syncdb`：

    ![主控台](media/template-django-console-sync-db.png)

- **收集靜態**：執行 `manage.py collectstatic --noinput` 以將所有靜態檔案複製到由 *settings.py* 中的 `STATIC_ROOT` 所指定的路徑。 當您[發行至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md) 時，系統會自動收集靜態檔案作為發佈作業的一部分。

    ![主控台](media/template-django-console-collect-static.png)

- **驗證**：執行 `manage.py validate`，這會報告由 *settings.py* 中的 `INSTALLED_APPS` 所指定之已安裝模型中的所有驗證錯誤：

    ![主控台](media/template-django-console-validate.png)

## <a name="see-also"></a>另請參閱

- [學習 Django 教學課程](learn-django-in-visual-studio-step-01-project-and-solution.md)
- [發佈至 Azure App Service](publishing-python-web-applications-to-azure-from-visual-studio.md)