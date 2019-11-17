---
author: Eirik Tenold
title: Java 8 and Play Framework 2.2.x
tags:
- Java
- Java 8
- Play Framework
---

In order for [Play Framework](http://www.playframework.com/) to work with Java 8, some changes has to be done:

In *build.sbt* add *scalaVersion := "2.10.3"* and change *sbt.version* to *0.13.1* in *project/build.properties*

If this is not done, you can get exceptions like

    java.lang.RuntimeException: Unknown constant: 18
     at scala.sys.package$.error(package.scala:27)
     at sbt.classfile.Parser$.getConstant(Parser.scala:150)
     at sbt.classfile.Parser$.parse$1(Parser.scala:127)
     at sbt.classfile.Parser$.sbt$classfile$Parser$$parseConstantPool(Parser.scala:132)
     at sbt.classfile.Parser$$anon$1.&lt;init&gt;(Parser.scala:32)
     at sbt.classfile.Parser$.parseImpl(Parser.scala:24)
     at sbt.classfile.Parser$.sbt$classfile$Parser$$parse(Parser.scala:20)
     at sbt.classfile.Parser$$anonfun$apply$1.apply(Parser.scala:19)
     at sbt.classfile.Parser$$anonfun$apply$1.apply(Parser.scala:19)
     at sbt.Using.apply(Using.scala:25)
     at sbt.classfile.Parser$.apply(Parser.scala:19)
     at sbt.classfile.Analyze$$anonfun$apply$2.apply(Analyze.scala:32)
     at sbt.classfile.Analyze$$anonfun$apply$2.apply(Analyze.scala:31)
     at scala.collection.TraversableLike$$anonfun$map$1.apply(TraversableLike.scala:244)
     at scala.collection.TraversableLike$$anonfun$map$1.apply(TraversableLike.scala:244)
     at scala.collection.mutable.ResizableArray$class.foreach(ResizableArray.scala:59)
     at scala.collection.mutable.ArrayBuffer.foreach(ArrayBuffer.scala:47)
     at scala.collection.TraversableLike$class.map(TraversableLike.scala:244)
     at scala.collection.AbstractTraversable.map(Traversable.scala:105)
     at sbt.classfile.Analyze$.apply(Analyze.scala:31)
     at sbt.compiler.AggressiveCompile$$anonfun$3$$anonfun$compileJava$1$2$$anonfun$apply$mcV$sp$2.apply(AggressiveCompile.scala:138)
     at sbt.compiler.AggressiveCompile$$anonfun$3$$anonfun$compileJava$1$2$$anonfun$apply$mcV$sp$2.apply(AggressiveCompile.scala:136)
     at scala.collection.TraversableLike$WithFilter$$anonfun$foreach$1.apply(TraversableLike.scala:772)
     at scala.collection.immutable.List.foreach(List.scala:318)
     at scala.collection.TraversableLike$WithFilter.foreach(TraversableLike.scala:771)
     at sbt.compiler.AggressiveCompile$$anonfun$3$$anonfun$compileJava$1$2.apply$mcV$sp(AggressiveCompile.scala:136)
     at sbt.compiler.AggressiveCompile$$anonfun$3$$anonfun$compileJava$1$2.apply(AggressiveCompile.scala:136)
     at sbt.compiler.AggressiveCompile$$anonfun$3$$anonfun$compileJava$1$2.apply(AggressiveCompile.scala:136)
     at sbt.compiler.AggressiveCompile.sbt$compiler$AggressiveCompile$$timed(AggressiveCompile.scala:159)
     at sbt.compiler.AggressiveCompile$$anonfun$3.compileJava$1(AggressiveCompile.scala:135)
     at sbt.compiler.AggressiveCompile$$anonfun$3.apply(AggressiveCompile.scala:142)
     at sbt.compiler.AggressiveCompile$$anonfun$3.apply(AggressiveCompile.scala:86)
     at sbt.inc.IncrementalCompile$$anonfun$doCompile$1.apply(Compile.scala:38)
     at sbt.inc.IncrementalCompile$$anonfun$doCompile$1.apply(Compile.scala:36)
     at sbt.inc.Incremental$.cycle(Incremental.scala:73)
     at sbt.inc.Incremental$$anonfun$1.apply(Incremental.scala:33)
     at sbt.inc.Incremental$$anonfun$1.apply(Incremental.scala:32)
     at sbt.inc.Incremental$.manageClassfiles(Incremental.scala:41)
     at sbt.inc.Incremental$.compile(Incremental.scala:32)
     at sbt.inc.IncrementalCompile$.apply(Compile.scala:26)
     at sbt.compiler.AggressiveCompile.compile2(AggressiveCompile.scala:150)
     at sbt.compiler.AggressiveCompile.compile1(AggressiveCompile.scala:70)
     at sbt.compiler.AggressiveCompile.apply(AggressiveCompile.scala:45)
     at sbt.Compiler$.apply(Compiler.scala:70)
     at sbt.Defaults$.sbt$Defaults$$compileTaskImpl(Defaults.scala:722)
     at sbt.Defaults$$anonfun$compileTask$1.apply(Defaults.scala:716)
     at sbt.Defaults$$anonfun$compileTask$1.apply(Defaults.scala:716)
     at scala.Function1$$anonfun$compose$1.apply(Function1.scala:47)
     at sbt.$tilde$greater$$anonfun$$u2219$1.apply(TypeFunctions.scala:42)
     at sbt.std.Transform$$anon$4.work(System.scala:64)
     at sbt.Execute$$anonfun$submit$1$$anonfun$apply$1.apply(Execute.scala:237)
     at sbt.Execute$$anonfun$submit$1$$anonfun$apply$1.apply(Execute.scala:237)
     at sbt.ErrorHandling$.wideConvert(ErrorHandling.scala:18)
     at sbt.Execute.work(Execute.scala:244)
     at sbt.Execute$$anonfun$submit$1.apply(Execute.scala:237)
     at sbt.Execute$$anonfun$submit$1.apply(Execute.scala:237)
     at sbt.ConcurrentRestrictions$$anon$4$$anonfun$1.apply(ConcurrentRestrictions.scala:160)
     at sbt.CompletionService$$anon$2.call(CompletionService.scala:30)
     at java.util.concurrent.FutureTask.run(FutureTask.java:266)
     at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
     at java.util.concurrent.FutureTask.run(FutureTask.java:266)
     at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
     at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
     at java.lang.Thread.run(Thread.java:744)</blockquote>