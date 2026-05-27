<!--
Licensed to the Apache Software Foundation (ASF) under one or more
contributor license agreements.  See the NOTICE file distributed with
this work for additional information regarding copyright ownership.
The ASF licenses this file to you under the Apache License, Version 2.0
(the "License"); you may not use this file except in compliance with
the License.  You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

# Agent instructions

## Cursor Cloud specific instructions

- This is a Java 21 / Maven monorepo. The core end-to-end development stack is documented in `packaging/src/docker/README.md` and runs Postgres, Hive Metastore, and HiveServer2 from `packaging/src/docker/docker-compose.yml`.
- In Cursor Cloud, Docker commands may require `sudo` even when the Docker CLI is installed. If the daemon is not running, start it in a persistent shell/tmux session before using Compose.
- The Docker Compose stack requires `HIVE_VERSION` and `POSTGRES_LOCAL_PATH`; the VM startup update script refreshes the PostgreSQL JDBC artifact, so `POSTGRES_LOCAL_PATH` can be derived from Maven's local repository as shown in `packaging/src/docker/README.md`.
- The optional LLAP, Ozone, Polaris, Gravitino, Kubernetes operator, and storage-handler stacks are separate integration surfaces; keep them opt-in unless the task explicitly targets those flows.
