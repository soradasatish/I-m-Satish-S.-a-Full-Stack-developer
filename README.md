name: I-m-Satish-S.-a-Full-Stack-developer
on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:

    runs-on: atom-latest

    steps:
    - uses: actions/checkout@v3
    - name: Build the site in the satishs/builder container
      run: |
        docker run \
        -v ${{ github.workspace }}:/srv/satishs -v ${{ github.workspace }}/_site:/srv/satishs/_site \
       satishs/builder:latest /bin/bash -c "chmod -R 777 /srv/satishs && satishs build --future"
