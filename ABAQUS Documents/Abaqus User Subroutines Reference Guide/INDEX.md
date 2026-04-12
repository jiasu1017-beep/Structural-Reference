# Abaqus User Subroutines Reference Guide

## Abaqus 用户子程序参考指南

**来源 / Source:** D:\SIMULIA\Documentation\docs\v6.14\books\usb

---

## Part I: Writing User Subroutines / 第一部分：编写用户子程序

### 1. Introduction / 简介

| 英文 English | 中文 Chinese | 说明 Note |
|-------------|-------------|----------|
| [pt01ch01.md](./eng/pt01ch01.md) | [pt01ch01.md](./chs/pt01ch01.md) | 1.1 About Abaqus / 关于 Abaqus |
| [pt01ch01s01.md](./eng/pt01ch01s01.md) | [pt01ch01s01.md](./chs/pt01ch01s01.md) | 1.1.1 Abaqus Overview / Abaqus 概述 |
| [pt01ch01s01abo01.md](./eng/pt01ch01s01abo01.md) | [pt01ch01s01abo01.md](./chs/pt01ch01s01abo01.md) | 1.1.1.1 Abaqus/Standard and Abaqus/Explicit / Abaqus/Standard 与 Abaqus/Explicit |
| [pt01ch01s02.md](./eng/pt01ch01s02.md) | [pt01ch01s02.md](./chs/pt01ch01s02.md) | 1.1.2 Abaqus/CAE |
| [pt01ch01s02aus01.md](./eng/pt01ch01s02aus01.md) | [pt01ch01s02aus01.md](./chs/pt01ch01s02aus01.md) | 1.1.2.1 |
| [pt01ch01s02aus02.md](./eng/pt01ch01s02aus02.md) | [pt01ch01s02aus02.md](./chs/pt01ch01s02aus02.md) | 1.1.2.2 |
| [pt01ch01s03.md](./eng/pt01ch01s03.md) | [pt01ch01s03.md](./chs/pt01ch01s03.md) | 1.1.3 Abaqus/Design |
| [pt01ch01s03aus03.md](./eng/pt01ch01s03aus03.md) | [pt01ch01s03aus03.md](./chs/pt01ch01s03aus03.md) | 1.1.3.1 |
| [pt01ch01s04.md](./eng/pt01ch01s04.md) | [pt01ch01s04.md](./chs/pt01ch01s04.md) | 1.1.4 Abaqus/Make |
| [pt01ch01s04aus04.md](./eng/pt01ch01s04aus04.md) | [pt01ch01s04aus04.md](./chs/pt01ch01s04aus04.md) | 1.1.4.1 |
| [pt01ch02.md](./eng/pt01ch02.md) | [pt01ch02.md](./chs/pt01ch02.md) | 1.2 Abaqus/Standard user subroutines / Abaqus/Standard 用户子程序 |
| [pt01ch02s01.md](./eng/pt01ch02s01.md) | [pt01ch02s01.md](./chs/pt01ch02s01.md) | 1.2.1 |
| [pt01ch02s01aus05.md](./eng/pt01ch02s01aus05.md) | [pt01ch02s01aus05.md](./chs/pt01ch02s01aus05.md) | 1.2.1.1 |
| [pt01ch02s01aus06.md](./eng/pt01ch02s01aus06.md) | [pt01ch02s01aus06.md](./chs/pt01ch02s01aus06.md) | 1.2.1.2 |
| [pt01ch02s01aus07.md](./eng/pt01ch02s01aus07.md) | [pt01ch02s01aus07.md](./chs/pt01ch02s01aus07.md) | 1.2.1.3 |
| [pt01ch02s01aus08.md](./eng/pt01ch02s01aus08.md) | [pt01ch02s01aus08.md](./chs/pt01ch02s01aus08.md) | 1.2.1.4 |
| [pt01ch02s01aus09.md](./eng/pt01ch02s01aus09.md) | [pt01ch02s01aus09.md](./chs/pt01ch02s01aus09.md) | 1.2.1.5 |
| [pt01ch02s01aus10.md](./eng/pt01ch02s01aus10.md) | [pt01ch02s01aus10.md](./chs/pt01ch02s01aus10.md) | 1.2.1.6 |
| [pt01ch02s02.md](./eng/pt01ch02s02.md) | [pt01ch02s02.md](./chs/pt01ch02s02.md) | 1.2.2 |
| [pt01ch02s02aus11.md](./eng/pt01ch02s02aus11.md) | [pt01ch02s02aus11.md](./chs/pt01ch02s02aus11.md) | 1.2.2.1 |
| [pt01ch02s02aus12.md](./eng/pt01ch02s02aus12.md) | [pt01ch02s02aus12.md](./chs/pt01ch02s02aus12.md) | 1.2.2.2 |
| [pt01ch02s02aus13.md](./eng/pt01ch02s02aus13.md) | [pt01ch02s02aus13.md](./chs/pt01ch02s02aus13.md) | 1.2.2.3 |
| [pt01ch02s02aus14.md](./eng/pt01ch02s02aus14.md) | [pt01ch02s02aus14.md](./chs/pt01ch02s02aus14.md) | 1.2.2.4 |
| [pt01ch02s02aus15.md](./eng/pt01ch02s02aus15.md) | [pt01ch02s02aus15.md](./chs/pt01ch02s02aus15.md) | 1.2.2.5 |
| [pt01ch02s03.md](./eng/pt01ch02s03.md) | [pt01ch02s03.md](./chs/pt01ch02s03.md) | 1.2.3 |
| [pt01ch02s03aus16.md](./eng/pt01ch02s03aus16.md) | [pt01ch02s03aus16.md](./chs/pt01ch02s03aus16.md) | 1.2.3.1 |
| [pt01ch02s03aus17.md](./eng/pt01ch02s03aus17.md) | [pt01ch02s03aus17.md](./chs/pt01ch02s03aus17.md) | 1.2.3.2 |
| [pt01ch02s03aus18.md](./eng/pt01ch02s03aus18.md) | [pt01ch02s03aus18.md](./chs/pt01ch02s03aus18.md) | 1.2.3.3 |
| [pt01ch02s03aus19.md](./eng/pt01ch02s03aus19.md) | [pt01ch02s03aus19.md](./chs/pt01ch02s03aus19.md) | 1.2.3.4 |
| [pt01ch02s03aus20.md](./eng/pt01ch02s03aus20.md) | [pt01ch02s03aus20.md](./chs/pt01ch02s03aus20.md) | 1.2.3.5 |
| [pt01ch02s03aus21.md](./eng/pt01ch02s03aus21.md) | [pt01ch02s03aus21.md](./chs/pt01ch02s03aus21.md) | 1.2.3.6 |
| [pt01ch02s04.md](./eng/pt01ch02s04.md) | [pt01ch02s04.md](./chs/pt01ch02s04.md) | 1.2.4 |
| [pt01ch02s04aus22.md](./eng/pt01ch02s04aus22.md) | [pt01ch02s04aus22.md](./chs/pt01ch02s04aus22.md) | 1.2.4.1 |
| [pt01ch02s05.md](./eng/pt01ch02s05.md) | [pt01ch02s05.md](./chs/pt01ch02s05.md) | 1.2.5 |
| [pt01ch02s05aus23.md](./eng/pt01ch02s05aus23.md) | [pt01ch02s05aus23.md](./chs/pt01ch02s05aus23.md) | 1.2.5.1 |
| [pt01ch02s06.md](./eng/pt01ch02s06.md) | [pt01ch02s06.md](./chs/pt01ch02s06.md) | 1.2.6 |
| [pt01ch02s06aus24.md](./eng/pt01ch02s06aus24.md) | [pt01ch02s06aus24.md](./chs/pt01ch02s06aus24.md) | 1.2.6.1 |
| [pt01ch02s07.md](./eng/pt01ch02s07.md) | [pt01ch02s07.md](./chs/pt01ch02s07.md) | 1.2.7 |
| [pt01ch02s07aus25.md](./eng/pt01ch02s07aus25.md) | [pt01ch02s07aus25.md](./chs/pt01ch02s07aus25.md) | 1.2.7.1 |
| [pt01ch02s08.md](./eng/pt01ch02s08.md) | [pt01ch02s08.md](./chs/pt01ch02s08.md) | 1.2.8 |
| [pt01ch02s08aus26.md](./eng/pt01ch02s08aus26.md) | [pt01ch02s08aus26.md](./chs/pt01ch02s08aus26.md) | 1.2.8.1 |
| [pt01ch02s09.md](./eng/pt01ch02s09.md) | [pt01ch02s09.md](./chs/pt01ch02s09.md) | 1.2.9 |
| [pt01ch02s09aus27.md](./eng/pt01ch02s09aus27.md) | [pt01ch02s09aus27.md](./chs/pt01ch02s09aus27.md) | 1.2.9.1 |
| [pt01ch02s10.md](./eng/pt01ch02s10.md) | [pt01ch02s10.md](./chs/pt01ch02s10.md) | 1.2.10 |
| [pt01ch02s10aus28.md](./eng/pt01ch02s10aus28.md) | [pt01ch02s10aus28.md](./chs/pt01ch02s10aus28.md) | 1.2.10.1 |
| [pt01ch02s11.md](./eng/pt01ch02s11.md) | [pt01ch02s11.md](./chs/pt01ch02s11.md) | 1.2.11 |
| [pt01ch02s11aus29.md](./eng/pt01ch02s11aus29.md) | [pt01ch02s11aus29.md](./chs/pt01ch02s11aus29.md) | 1.2.11.1 |
| [pt01ch03.md](./eng/pt01ch03.md) | [pt01ch03.md](./chs/pt01ch03.md) | 1.3 Abaqus/Explicit user subroutines / Abaqus/Explicit 用户子程序 |
| [pt01ch03s01.md](./eng/pt01ch03s01.md) | [pt01ch03s01.md](./chs/pt01ch03s01.md) | 1.3.1 |
| [pt01ch03s01abo02.md](./eng/pt01ch03s01abo02.md) | [pt01ch03s01abo02.md](./chs/pt01ch03s01abo02.md) | 1.3.1.1 |
| [pt01ch03s02.md](./eng/pt01ch03s02.md) | [pt01ch03s02.md](./chs/pt01ch03s02.md) | 1.3.2 |
| [pt01ch03s02abx01.md](./eng/pt01ch03s02abx01.md) | [pt01ch03s02abx01.md](./chs/pt01ch03s02abx01.md) | 1.3.2.1 VUMAT |
| [pt01ch03s02abx02.md](./eng/pt01ch03s02abx02.md) | [pt01ch03s02abx02.md](./chs/pt01ch03s02abx02.md) | 1.3.2.2 VUMAT for Gurson-Tvergaard model / Gurson-Tvergaard 模型 VUMAT |
| [pt01ch03s02abx03.md](./eng/pt01ch03s02abx03.md) | [pt01ch03s02abx03.md](./chs/pt01ch03s02abx03.md) | 1.3.2.3 |
| [pt01ch03s02abx04.md](./eng/pt01ch03s02abx04.md) | [pt01ch03s02abx04.md](./chs/pt01ch03s02abx04.md) | 1.3.2.4 |
| [pt01ch03s02abx05.md](./eng/pt01ch03s02abx05.md) | [pt01ch03s02abx05.md](./chs/pt01ch03s02abx05.md) | 1.3.2.5 |
| [pt01ch03s02abx06.md](./eng/pt01ch03s02abx06.md) | [pt01ch03s02abx06.md](./chs/pt01ch03s02abx06.md) | 1.3.2.6 |
| [pt01ch03s02abx07.md](./eng/pt01ch03s02abx07.md) | [pt01ch03s02abx07.md](./chs/pt01ch03s02abx07.md) | 1.3.2.7 |
| [pt01ch03s02abx08.md](./eng/pt01ch03s02abx08.md) | [pt01ch03s02abx08.md](./chs/pt01ch03s02abx08.md) | 1.3.2.8 |
| [pt01ch03s02abx09.md](./eng/pt01ch03s02abx09.md) | [pt01ch03s02abx09.md](./chs/pt01ch03s02abx09.md) | 1.3.2.9 |
| [pt01ch03s02abx10.md](./eng/pt01ch03s02abx10.md) | [pt01ch03s02abx10.md](./chs/pt01ch03s02abx10.md) | 1.3.2.10 |
| [pt01ch03s02abx11.md](./eng/pt01ch03s02abx11.md) | [pt01ch03s02abx11.md](./chs/pt01ch03s02abx11.md) | 1.3.2.11 |
| [pt01ch03s02abx12.md](./eng/pt01ch03s02abx12.md) | [pt01ch03s02abx12.md](./chs/pt01ch03s02abx12.md) | 1.3.2.12 |
| [pt01ch03s02abx13.md](./eng/pt01ch03s02abx13.md) | [pt01ch03s02abx13.md](./chs/pt01ch03s02abx13.md) | 1.3.2.13 |
| [pt01ch03s02abx14.md](./eng/pt01ch03s02abx14.md) | [pt01ch03s02abx14.md](./chs/pt01ch03s02abx14.md) | 1.3.2.14 |
| [pt01ch03s02abx15.md](./eng/pt01ch03s02abx15.md) | [pt01ch03s02abx15.md](./chs/pt01ch03s02abx15.md) | 1.3.2.15 |
| [pt01ch03s02abx16.md](./eng/pt01ch03s02abx16.md) | [pt01ch03s02abx16.md](./chs/pt01ch03s02abx16.md) | 1.3.2.16 |
| [pt01ch03s02abx17.md](./eng/pt01ch03s02abx17.md) | [pt01ch03s02abx17.md](./chs/pt01ch03s02abx17.md) | 1.3.2.17 |
| [pt01ch03s02abx18.md](./eng/pt01ch03s02abx18.md) | [pt01ch03s02abx18.md](./chs/pt01ch03s02abx18.md) | 1.3.2.18 |
| [pt01ch03s02abx19.md](./eng/pt01ch03s02abx19.md) | [pt01ch03s02abx19.md](./chs/pt01ch03s02abx19.md) | 1.3.2.19 |
| [pt01ch03s02abx20.md](./eng/pt01ch03s02abx20.md) | [pt01ch03s02abx20.md](./chs/pt01ch03s02abx20.md) | 1.3.2.20 |
| [pt01ch03s02abx21.md](./eng/pt01ch03s02abx21.md) | [pt01ch03s02abx21.md](./chs/pt01ch03s02abx21.md) | 1.3.2.21 |
| [pt01ch03s02abx22.md](./eng/pt01ch03s02abx22.md) | [pt01ch03s02abx22.md](./chs/pt01ch03s02abx22.md) | 1.3.2.22 |
| [pt01ch03s02abx23.md](./eng/pt01ch03s02abx23.md) | [pt01ch03s02abx23.md](./chs/pt01ch03s02abx23.md) | 1.3.2.23 |
| [pt01ch03s02abx24.md](./eng/pt01ch03s02abx24.md) | [pt01ch03s02abx24.md](./chs/pt01ch03s02abx24.md) | 1.3.2.24 |
| [pt01ch03s02abx25.md](./eng/pt01ch03s02abx25.md) | [pt01ch03s02abx25.md](./chs/pt01ch03s02abx25.md) | 1.3.2.25 |
| [pt01ch03s02abx26.md](./eng/pt01ch03s02abx26.md) | [pt01ch03s02abx26.md](./chs/pt01ch03s02abx26.md) | 1.3.2.26 |
| [pt01ch03s02abx27.md](./eng/pt01ch03s02abx27.md) | [pt01ch03s02abx27.md](./chs/pt01ch03s02abx27.md) | 1.3.2.27 |
| [pt01ch03s02abx28.md](./eng/pt01ch03s02abx28.md) | [pt01ch03s02abx28.md](./chs/pt01ch03s02abx28.md) | 1.3.2.28 |
| [pt01ch03s02abx29.md](./eng/pt01ch03s02abx29.md) | [pt01ch03s02abx29.md](./chs/pt01ch03s02abx29.md) | 1.3.2.29 |
| [pt01ch03s02abx30.md](./eng/pt01ch03s02abx30.md) | [pt01ch03s02abx30.md](./chs/pt01ch03s02abx30.md) | 1.3.2.30 |
| [pt01ch03s02abx31.md](./eng/pt01ch03s02abx31.md) | [pt01ch03s02abx31.md](./chs/pt01ch03s02abx31.md) | 1.3.2.31 |
| [pt01ch03s02abx32.md](./eng/pt01ch03s02abx32.md) | [pt01ch03s02abx32.md](./chs/pt01ch03s02abx32.md) | 1.3.2.32 |
| [pt01ch03s02abx33.md](./eng/pt01ch03s02abx33.md) | [pt01ch03s02abx33.md](./chs/pt01ch03s02abx33.md) | 1.3.2.33 |
| [pt01ch03s02abx34.md](./eng/pt01ch03s02abx34.md) | [pt01ch03s02abx34.md](./chs/pt01ch03s02abx34.md) | 1.3.2.34 |
| [pt01ch03s02abx35.md](./eng/pt01ch03s02abx35.md) | [pt01ch03s02abx35.md](./chs/pt01ch03s02abx35.md) | 1.3.2.35 |
| [pt01ch03s02abx36.md](./eng/pt01ch03s02abx36.md) | [pt01ch03s02abx36.md](./chs/pt01ch03s02abx36.md) | 1.3.2.36 |
| [pt01ch03s02abx37.md](./eng/pt01ch03s02abx37.md) | [pt01ch03s02abx37.md](./chs/pt01ch03s02abx37.md) | 1.3.2.37 |
| [pt01ch03s02abx38.md](./eng/pt01ch03s02abx38.md) | [pt01ch03s02abx38.md](./chs/pt01ch03s02abx38.md) | 1.3.2.38 |
| [pt01ch03s02abx39.md](./eng/pt01ch03s02abx39.md) | [pt01ch03s02abx39.md](./chs/pt01ch03s02abx39.md) | 1.3.2.39 |
| [pt01ch03s03.md](./eng/pt01ch03s03.md) | [pt01ch03s03.md](./chs/pt01ch03s03.md) | 1.3.3 |
| [pt01ch03s03aus30.md](./eng/pt01ch03s03aus30.md) | [pt01ch03s03aus30.md](./chs/pt01ch03s03aus30.md) | 1.3.3.1 |
| [pt01ch03s04.md](./eng/pt01ch03s04.md) | [pt01ch03s04.md](./chs/pt01ch03s04.md) | 1.3.4 |
| [pt01ch03s04aus31.md](./eng/pt01ch03s04aus31.md) | [pt01ch03s04aus31.md](./chs/pt01ch03s04aus31.md) | 1.3.4.1 |
| [pt01ch03s05.md](./eng/pt01ch03s05.md) | [pt01ch03s05.md](./chs/pt01ch03s05.md) | 1.3.5 |
| [pt01ch03s05aus32.md](./eng/pt01ch03s05aus32.md) | [pt01ch03s05aus32.md](./chs/pt01ch03s05aus32.md) | 1.3.5.1 |
| [pt01ch03s05aus33.md](./eng/pt01ch03s05aus33.md) | [pt01ch03s05aus33.md](./chs/pt01ch03s05aus33.md) | 1.3.5.2 |
| [pt01ch03s05aus34.md](./eng/pt01ch03s05aus34.md) | [pt01ch03s05aus34.md](./chs/pt01ch03s05aus34.md) | 1.3.5.3 |
| [pt01ch03s05aus35.md](./eng/pt01ch03s05aus35.md) | [pt01ch03s05aus35.md](./chs/pt01ch03s05aus35.md) | 1.3.5.4 |
| [pt01ch03s06.md](./eng/pt01ch03s06.md) | [pt01ch03s06.md](./chs/pt01ch03s06.md) | 1.3.6 |
| [pt01ch03s06aus36.md](./eng/pt01ch03s06aus36.md) | [pt01ch03s06aus36.md](./chs/pt01ch03s06aus36.md) | 1.3.6.1 |
| [pt01ch03s07.md](./eng/pt01ch03s07.md) | [pt01ch03s07.md](./chs/pt01ch03s07.md) | 1.3.7 |
| [pt01ch03s07aus37.md](./eng/pt01ch03s07aus37.md) | [pt01ch03s07aus37.md](./chs/pt01ch03s07aus37.md) | 1.3.7.1 |

### 2. Abaqus/Standard Subroutines / Abaqus/Standard 子程序

(735 total files - full index in [eng/](./eng/) directory)

---

## 转换状态 / Conversion Status

| 状态 Status | 数量 Count |
|-------------|------------|
| ✅ 英文已转换 / English converted | 735 |
| ⏳ 中文翻译中 / Chinese translating | 0 |
| ✅ 中文已完成 / Chinese completed | 0 |

**总计 / Total:** 735 files

---

## 版权声明 / Copyright Notice

本翻译仅供学习研究使用，原文档版权归 Dassault Systèmes Simulia Corp. 所有。

This translation is for study and research purposes only. Original documentation copyright Dassault Systèmes Simulia Corp.
