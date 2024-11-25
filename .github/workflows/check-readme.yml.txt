name: Egocentric Commit Check

run-name: ${{ github.actor }} is ensuring their name is in the README 

on: [commit]

jobs:
  Check-My-Name-In-README:
    runs-on: ubuntu-latest

    steps:
      - run: echo " Checking if the README.md file contains the 	required name."

      - name: Check out repository code
        uses: actions/checkout@v4

      - name: Verify Name in README.md
        run: |
          if ! grep -q "Rachele" README.md; then
            echo " README.md does not contain the required name. Commit rejected."
            exit 1
          fi
          echo " README.md contains the required name. Commit accepted."

      - run: echo " This job's status is ${{ job.status }}."