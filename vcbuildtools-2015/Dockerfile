FROM microsoft/windowsservercore:1803

# Install chocolatey
RUN @powershell -NoProfile -ExecutionPolicy unrestricted -Command "(iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))) >$null 2>&1"

# Install Visual Studio 2015, Python3, CMake, Git and Conan
RUN choco install -y visualcppbuildtools -packageParameters "--Features Windows10_ToolsAndSDKV13" \
    && choco install python -y \
    && choco install cmake --installargs 'ADD_CMAKE_TO_PATH=System' -y \
    && choco install git -y \
    && RefreshEnv \
    && pip install conan \
    && pip install conan_package_tools

# Conan environment configuration
RUN setx /M CONAN_VISUAL_VERSIONS 14 \
    && setx /M CONAN_ARCHS x86_64 \
    && setx /M CONAN_VISUAL_RUNTIMES MD \
    && setx /M CONAN_REMOTES http://5.39.78.163:8081/artifactory/api/conan/conan-local@False@fw4spl-conan \
    && setx /M CONAN_UPLOAD http://5.39.78.163:8081/artifactory/api/conan/conan-local

WORKDIR C:\\build
CMD [ "cmd.exe" ]