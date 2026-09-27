# Dockerfile Instructions Reference

Reference examples for each **Dockerfile instruction**. Each subdirectory demonstrates one instruction in isolation — perfect for learning and testing specific Dockerfile behaviors.

## Structure

```
dockerfiles/
├── ADD/Dockerfile          # ADD instruction (copy files + auto-extract tar)
├── ADD/sample-1.tar        # Test archive for ADD
├── ARG/Dockerfile          # ARG instruction (build-time variables)
├── CMD/dockerfile          # CMD instruction (default command)
├── COPY/Dockerfile         # COPY instruction (copy files)
├── COPY/index.html         # Test file for COPY
├── ENTRYPOINT/Dockerfile   # ENTRYPOINT instruction (main command)
├── ENV/Dockerfile          # ENV instruction (environment variables)
├── EXPOSE/Dockerfile       # EXPOSE instruction (documented ports)
├── FROM/dockerfile         # FROM instruction (base image)
├── LABEL/dockerfile        # LABEL instruction (metadata)
├── ONBUILD/Dockerfile      # ONBUILD instruction (trigger on child builds)
├── ONBUILD/TEST/Dockerfile # Child Dockerfile for ONBUILD testing
├── ONBUILD/TEST/index.html # Test file for ONBUILD
├── RUN/dockerfile          # RUN instruction (execute commands)
├── USER/Dockerfile         # USER instruction (run as non-root)
└── WORKDIR/Dockerfile      # WORKDIR instruction (working directory)
```

## Instructions Covered

| Instruction | Purpose | Key Demo |
|---|---|---|
| `FROM` | Base image selection | Minimal base image |
| `RUN` | Build-time commands | Package install, file creation |
| `CMD` | Default container command | Overridable defaults |
| `ENTRYPOINT` | Fixed container command | Arguments passed to entrypoint |
| `COPY` | Copy files to image | Local file → image |
| `ADD` | Copy + extract archives | `.tar` auto-extraction |
| `ENV` | Set environment variables | Build-time + runtime |
| `ARG` | Build-time variables | `docker build --build-arg` |
| `EXPOSE` | Document ports | Port documentation |
| `WORKDIR` | Set working directory | Nested paths |
| `USER` | Run as non-root | Security best practice |
| `LABEL` | Add metadata | Image annotations |
| `ONBUILD` | Deferred execution | Trigger on child `FROM` |

## Quick Start

```bash
# Test any instruction
docker build -t test-run ./RUN
docker run test-run

# Test ONBUILD (two-step)
docker build -t onbuild-parent ./ONBUILD
docker build -t onbuild-child ./ONBUILD/TEST
docker run onbuild-child
```

## Learning Path

1. Start with `FROM` → `RUN` → `CMD`/`ENTRYPOINT`
2. Move to `COPY` vs `ADD`, `WORKDIR`, `ENV`/`ARG`
3. Practice `USER` for security
4. Advanced: `ONBUILD` for base image patterns