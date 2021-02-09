---
title: 快速入門 - 使用範本建立 Python 專案
description: 在此快速入門中，您可以使用基本 Flask 應用程式的內建範本來建立 Python 的 Visual Studio 專案。
ms.date: 12/06/2018
ms.topic: quickstart
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 81f337cf3feca517f46632e7fe08a9f5a62cd707
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902444"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>快速入門：在 Visual Studio 中從範本建立 Python 專案

[在 Visual Studio 中安裝 Python 支援](installing-python-support-in-visual-studio.md)之後，就可以使用各種範本輕鬆地建立新的 Python 專案。 在此快速入門中，您可以使用範本建立簡單的 Flask 應用程式。 產生的專案類似於您透過[快速入門 - 使用 Flask 建立 Web 應用程式](../ide/quickstart-python.md)手動建立的專案。

1. 啟動 Visual Studio。

1. 從頂端功能表列中 **，選擇 [** 檔案  >  **新增**  >  **專案**]，然後在 [**新增專案**] 對話方塊中搜尋 [空白 flask]，選取中間清單中的 [**空白 flask Web 專案**] 範本，為專案命名，然後選取 **[確定]**：

    ![使用空白 Flask Web 專案範本建立新的專案](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio 會提示您一個對話方塊，指出 **此專案需要外部套件。** 出現此對話方塊的原因是該範本包含的 *requirements.txt* 檔案指定 Flask 的相依性。 Visual Studio 可自動安裝套件，並可讓您選擇將其安裝至「虛擬環境」。 建議使用虛擬環境而非安裝到全域環境，所以請選取 [安裝至虛擬環境] 以繼續進行。

    ![將 Flask 安裝至虛擬環境](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio 會顯示 [新增虛擬環境] 對話方塊。 接受預設值並選取 [建立]，然後同意任何提高權限要求。

    > [!Tip]
    > 當您開始專案時，強烈建議您立刻建立虛擬環境，因為大部分 Visual Studio 範本都會請您執行此作業。 當您新增或移除程式庫時，虛擬環境可持續維護您的專案實際需求。 您接著可以輕鬆地產生 *requirements.txt* 檔案，用來在其他開發電腦上 (使用原始檔控制時) 重新安裝那些相依性，以及在將專案部署到生產伺服器時使用。 如需虛擬環境與其優點的詳細資訊，請參閱[使用虛擬環境](../python/selecting-a-python-environment-for-a-project.md#use-virtual-environments)與[使用 requirements.txt 管理必要套件](../python/managing-required-packages-with-requirements-txt.md)。

1. 在 Visual Studio 建立環境之後，查看 [方案總管] 中是否可看到 *app.py* 檔案與 *requirements.txt*。 開啟 *app.py* 即可看到範本已提供和 [快速入門 - 使用 Flask 建立 Web 應用程式](../ide/quickstart-python.md)中程式碼類似的程式碼，並新增了幾個區段。 下方顯示的程式碼均由範本建立，因此您不必自行在 *app.py* 貼入任何程式碼。

    程式碼會從必要的匯入開始：

    ```python
    from flask import Flask
    app = Flask(__name__)
    ```

    接下來這行，在將應用程式部署到 Web 主機時相當實用：

    ```python
    wsgi_app = app.wsgi_app
    ```

    再來是簡單函式上的路由裝飾項目，以定義檢視：

    ```python
    @app.route('/')
    def hello():
        """Renders a sample page."""
        return "Hello World!"
    ```

    最後則是下方的啟動程式碼，可讓您透過環境變數來設定主機和連接埠，而不是對其寫入編碼。 此類程式碼可讓您輕鬆地控制開發和生產機器上的設定，而不需要變更程式碼：

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. 選取 **[**  >  **啟動時不進行調試** 程式] 來執行應用程式，並開啟瀏覽器 `localhost:5555` 。

**問題：Visual Studio 還提供其他哪些 Python 範本？**

**解答**：安裝 Python 工作負載後，Visual Studio 提供各種不同的專案範本，包括可用於 [Flask、Bottle 及 Django Web 架構](../python/python-web-application-project-templates.md)、Azure 雲端服務、不同機器學習案例，甚至還有範本可從包含 Python 應用程式的現有資料夾結構建立專案。 您可以 **透過 [檔案**  >  **新增**  >  **專案**] 對話方塊來存取這些專案，方法是選取 [ **Python** 語言] 節點及其子節點。

Visual Studio 也提供各種不同的檔案或 *專案範本* ，可快速建立 python 類別、python 套件、python 單元測試、 *web.config* 檔案等等。 當 Python 專案開啟時，您可以透過 [**專案**  >  **加入新專案**] 功能表命令來存取專案範本。 請參閱[項目範本](python-item-templates.md)參考。

開始專案或建立檔案時，使用範本可節省大量時間，而且這也是了解不同應用程式類型與程式碼結構的好方法。 花費幾分鐘的時間從不同的範本建立專案與項目，熟悉一下所提供的功能會很有幫助。

**問題：我是否也可以使用 Cookiecutter 範本？**

**答**：是！ 事實上，Visual Studio 提供與 Cookiecutter 的直接整合，您可以透過 [快速入門：從 Cookiecutter 範本建立專案](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md)。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [教學課程：在 Visual Studio 中使用 Python](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>另請參閱

- [手動識別現有的 Python 解譯器](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [在 Visual Studio 2015 及更早版本中安裝 Python 支援](installing-python-support-in-visual-studio.md)
- [安裝位置](installing-python-support-in-visual-studio.md#install-locations)
