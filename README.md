# WebIDE Development Environment (WebIDE开发环境)

Hello, welcome to our WebIDE Development Environment repository. This repository is committed to creating a Docker image of WebIDE integrated development environment, which is based on the basic image from code-server. With this image, developers can quickly enter the development environment without any additional configuration.

你好，欢迎来到我们的WebIDE开发环境仓库。本仓库致力于基于code-server基础镜像创建一个能够集成WebIDE开发环境的Docker镜像。有了这个镜像，开发者可以迅速进入开发环境，无需进行任何额外的配置。
## Current Image Content (当前镜像内容)
✅ python3.6 + pyenv + node18 -> cgh1999520/webide-py-node

## Future Extensions (未来扩展)
We're planning to integrate more development environments into this Docker image in the future. Stay tuned!

我们计划在未来将更多的开发环境整合到这个Docker镜像中。敬请期待！

## Getting Started (开始使用)

### Prerequisites (前期准备)

- Docker should be installed on your machine. If not, refer to: [Install Docker](https://docs.docker.com/get-docker/)

你的机器上应该安装有Docker。如果没有，请参考：[安装Docker](https://docs.docker.com/get-docker/)

### Usage (使用方法)

To launch the docker image:

为了启动docker镜像：

```bash
docker run -it --name code-server -p 127.0.0.1:8080:8080 \
  -v "$HOME/.local:/home/coder/.local" \
  -v "$HOME/.config:/home/coder/.config" \
  -v "$PWD:/home/coder/project" \
  -u "$(id -u):$(id -g)" \
  -e "DOCKER_USER=$USER" \
  cgh1999520/webide-py-node:latest

```

## Contribution (贡献)

We welcome contributions to enhance the Docker image. Here are the steps you can follow:

我们欢迎对增强Docker镜像的贡献。你可以遵循以下步骤：

```bash
1. Fork this repository
2. Create your feature branch (git checkout -b AmazingFeature)
3. Commit your changes (git commit -m 'Add some AmazingFeature')
4. Push your feature branch (git push origin AmazingFeature)
5. Open a pull request
```

## Authors (作者)

- 蔡昂 (AngCai)

## License (许可证)

This project is under the MIT License. For more details, see the LICENSE.md file in the repository.

本项目在MIT许可证下发布。更多详细信息，请参见仓库中的LICENSE.md文件。

## Contact (联系方式)

Email: cgh1999520@email.com

Let us know your suggestions and thoughts on this project!

告诉我们你对这个项目的建议和想法！
