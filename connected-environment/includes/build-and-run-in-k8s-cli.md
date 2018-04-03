## <a name="build-and-run-code-in-kubernetes"></a>在 Kubernetes 中建置並執行程式碼
開始執行我們的程式碼吧！ 在終端機視窗中，從**根程式碼資料夾**執行此命令，webfrontend：

```cmd
vsce up
```

請注意命令的輸出，它在執行時，您會發現幾件事：
1. 原始程式碼會同步至 Azure 的開發環境。
1. 容器映像是在 Azure 中建立，如您程式碼資料夾中的 Docker 資產所指定。
1. 建立的 Kubernetes 物件，會利用您程式碼資料夾中的 Helm 圖表所指定的容器映像。
1. 顯示容器端點的相關資訊。 在我們的案例中，應該是公用的 HTTPS URL。
1. 假設上述階段皆順利完成，您應該會隨著容器啟動開始看到 `stdout` (和 `stderr`) 輸出。

> [!Note]
> `up` 命令第一次執行時，這些步驟會需要較長的時間，但以後的執行應該會加快。

## <a name="test-the-web-app"></a>測試 Web 應用程式
掃描主控台輸出是否有 `up` 命令所建立的公用 URL 相關資訊。 它的格式如下： 

`Running at public URL: https://<servicename>-<environmentname>.vsce.io` 

在瀏覽器視窗中開啟此 URL，您應該會看到 Web 應用程式的載入過程。 當容器執行時，`stdout` 和 `stderr` 輸出會串流處理至終端機視窗。
