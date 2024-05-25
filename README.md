# PBRP Recovery Builder

This GitHub Actions workflow automates the compilation of PitchBlack Recovery Project (PBRP) images for Android devices.

## Workflow Dispatch

Triggered manually via the `workflow_dispatch` event with customizable inputs.

## Inputs Parameter Description

Here are the inputs required for the `PBRP-RECOVERY-BUILDER` workflow:

| Name | Description | Example |
| ---- | ----------- | ------- |
| `MANIFEST_URL` | Git URL of the PBRP manifest repository. | `https://github.com/PitchBlackRecoveryProject/manifest_pb.git` |
| `MANIFEST_BRANCH` | Branch name of the PBRP manifest to sync. | `android-11.0` |
| `DEVICE_TREE_URL` | Git URL of the device-specific repository. | `https://github.com/PitchBlackRecoveryProject/android_device_samsung_m21.git` |
| `DEVICE_TREE_BRANCH` | Branch name of the device-specific repository. | `android-11.0` |
| `DEVICE_PATH` | Directory path to clone the device tree into. | `device/samsung/m21` |
| `DEVICE_NAME` | Codename or model name of the device. | `m21` |
| `MAKEFILE_NAME` | Name of the makefile to initiate the build. | `pbrp_m21` |
| `BUILD_TARGET` | Target partition to build (e.g., boot, recovery, vendorboot). | `recovery` |
| `user` | Your GitHub username for commits. | `JohnDoe` |
| `USER_EMAIL` | Email address associated with your GitHub account. | `johndoe@example.com` |

## Jobs

### Build

Triggered by the repository owner and runs on the latest Ubuntu runner. It includes steps for setting up the environment, syncing repositories, compiling the recovery image, and uploading the build artifacts to a new release.

## Steps

1. **Display Run Parameters**: Outputs user-defined environment variables.
2. **Check Out**: Uses `actions/checkout@v4` to check out the repository.
3. **Cleanup**: Utilizes a custom action for workspace cleanup.
4. **Prepare the Environment**: Sets up the necessary build environment.
5. **Setup SSH Keys**: Configures SSH keys if required for private repositories.
6. **Install repo**: Installs the `repo` tool.
7. **Initialize repo**: Initializes the PBRP manifest repository.
8. **Repo Sync**: Synchronizes all repositories.
9. **Clone Device Tree**: Clones the device tree into the workspace.
10. **Set Swap Space**: Allocates swap space for the build.
11. **Building Recovery**: Executes the build process for PBRP.
12. **Upload to Release**: Uploads the built image to a GitHub release.

## Usage

To run the workflow:

1. Go to the `Actions` tab of the `PBRP-RECOVERY-BUILDER` repository.
2. Select the `Recovery Build` workflow.
3. Click on `Run workflow`.
4. Fill in the required fields with your specific build details.
5. Click `Run workflow` to start the build process.

## Notes

- Replace all `PLACEHOLDER` values with actual data relevant to your build.
- The workflow is configured for PBRP but can be adapted for other recovery projects as needed.
- Ensure your repository secrets are set up correctly for SSH keys and GitHub tokens.

## Credits

This project owes its existence to the contributions and efforts of many individuals and communities. We extend our sincere gratitude to everyone who has played a part in bringing this project to fruition.

Special thanks to:
- **ghazzor** for forking and modifying [Action-TWRP-Builder](https://github.com/azwhikaru/Action-TWRP-Builder) to build PBRP recovery and for providing the original workflow that served as the foundation for this project.
- **azwhikaru** for the original [Action-TWRP-Builder](https://github.com/azwhikaru) repository, which was forked and modified by ghazzor.

We also recognize the following for their support and contributions:
- The PitchBlack Recovery Project team for their outstanding contributions to the recovery development community.
- All developers and contributors who have contributed to device trees, kernels, and various scripts that streamline the building process.
- The GitHub community for providing a collaborative platform that unites developers from across the globe.

For more information on PBRP, visit the PitchBlack Recovery Project.