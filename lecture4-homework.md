# 第4课 课后作业

没什么操作的，直接使用官方文档搭建测试部署

```bash
(base) [root@localhost home]# npm i -g @semaphore-protocol/cli@latest

added 328 packages in 33s

70 packages are looking for funding
  run `npm fund` for details
(base) [root@localhost home]# semaphore create my-app --template monorepo-ethers

 ✔ Your project is ready!

 Please, install your dependencies by running:

   cd my-app
   npm i

 Available scripts:

   npm run dev
   npm run dev:web-app
   npm run dev:contracts
   npm run lint
   npm run prettier
   npm run prettier:write
   npm run copy:contract-artifacts
   npm run prepublish

 See the README.md file to understand how to use them!

(base) [root@localhost home]# cd my-app/
(base) [root@localhost my-app]# npm i
> @semaphore-protocol/cli-template-monorepo-ethers@3.10.1 prepublish
> tar -czf files.tgz .gitignore .yarn .yarnrc.yml apps
added 1567 packages, and audited 1570 packages in 2m
(base) [root@localhost contracts]# npm run compile

> monorepo-ethers-contracts@1.0.0 compile
> hardhat compile

Generating typings for: 12 artifacts in dir: ./build/typechain for target: ethers-v5
Successfully generated 40 typings!
Compiled 14 Solidity files successfully
(base) [root@localhost contracts]# btop
(base) [root@localhost contracts]# npm test

> monorepo-ethers-contracts@1.0.0 test
> hardhat run scripts/download-snark-artifacts.ts && hardhat test



  Feedback
    # joinGroup
      ✔ Should allow users to join the group (1780ms)
    # sendFeedback
      ✔ Should allow users to send feedback anonymously (4361ms)


  2 passing (11s)
(base) [root@localhost contracts]# npm run test:coverage

> monorepo-ethers-contracts@1.0.0 test:coverage
> hardhat coverage


Version
=======
> solidity-coverage: v0.7.22

Instrumenting for coverage...
=============================

> Feedback.sol

Compilation:
============

Generating typings for: 12 artifacts in dir: ./build/typechain for target: ethers-v5
Successfully generated 40 typings!

```
