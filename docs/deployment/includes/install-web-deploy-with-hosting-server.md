主控伺服器的 web Deploy 3.6 提供啟用的發佈設定檔，從 UI 建立的其他組態功能。

1. 如果您已經安裝在 Windows Server 上的 Web 部署 3.6，解除安裝使用它**控制台中** > **程式** > **解除安裝程式**.

2. 接下來，Web 部署 3.6 安裝在 Windows Server 上的主控伺服器。

    若要安裝 Web Deploy 主控伺服器，使用[Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx)。 (若要從 IIS 中尋找 Web Platform Installer 連結，請選取**IIS**伺服器管理員 的左窗格中。 以滑鼠右鍵按一下伺服器，然後選取**Internet Information Services (IIS) 管理員**。)

    在 Web Platform Installer 中，您發現**主控伺服器的 Web Deploy**應用程式 索引標籤中。

3. 如果您沒有已安裝**IIS 管理指令碼及工具**，立即安裝。

    移至**選取伺服器角色** > **網頁伺服器 (IIS)** > **管理工具**，然後選取 [ **IIS 管理指令碼和工具**角色中，按一下**下一步]**，然後再安裝角色。

    ![安裝 IIS 管理指令碼和工具](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    啟用的發佈設定檔產生所需的指令碼和工具。

4. （選擇性）確認 Web Deploy 正在執行正確 %installationdirectory**控制台 > 系統及安全性 > 系統管理工具 > 服務**並確定**Web Deployment Agent Service**執行 (服務名稱是在較舊版本不同）。

    如果未執行的代理程式服務，請加以啟動。 如果它根本不是存在，請移至**控制台 > 程式 > 解除安裝程式**，尋找**Microsoft Web Deploy <version>** 。 選擇**變更**安裝，並確定您選擇**將會安裝成在本機硬碟機**Web Deploy 的元件。 完成變更安裝的步驟。