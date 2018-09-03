FROM microsoft/windowsservercore:10.0.14393.1715

# Install chocolatey
RUN @powershell -NoProfile -ExecutionPolicy unrestricted -Command "(iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))) >$null 2>&1"

# Install Visual Studio 2017, Python3, CMake, Git and Conan
RUN choco install visualstudio2017buildtools -y \
    && choco install visualstudio2017-workload-vctools -y \
    && choco install python -y \
    && choco install cmake --installargs 'ADD_CMAKE_TO_PATH=System' -y \
    && choco install git -y \
    && RefreshEnv \
    && pip install conan \
    && pip install conan_package_tools

CMD [ "cmd.exe" ]