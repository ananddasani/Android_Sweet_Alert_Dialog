# Android_Sweet_Alert_Dialog
Using Library of Sweet Anim Dialogs

This topic is a part of [My Complete Andorid Course](https://github.com/ananddasani/Android_Apps)

# Code

#### MainActivity.java
```
public class MainActivity extends AppCompatActivity {
    private int i = -1;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        findViewById(R.id.underTest).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                showUnderTextDialog();
            }
        });

        findViewById(R.id.errorTest).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                showErrorTextDialog();
            }
        });

        findViewById(R.id.successTest).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                showSuccessTextDialog();
            }
        });

        findViewById(R.id.warningConfirm).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                showWarningConfirmDialog();
            }
        });

        findViewById(R.id.warningCancle).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                showWarningCancleDialog();
            }
        });

        findViewById(R.id.imageTest).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                showImageDialog();
            }
        });

        findViewById(R.id.progressDialog).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                showProgressDialog();
            }
        });
    }

    private void showProgressDialog() {

        final SweetAlertDialog pDialog = new SweetAlertDialog(this, SweetAlertDialog.PROGRESS_TYPE)
                .setTitleText("Loading");
        pDialog.show();
        pDialog.setCancelable(false);

        new CountDownTimer(800 * 7, 800) {
            public void onTick(long millisUntilFinished) {
                // you can change the progress bar color by ProgressHelper every 800 millis
                i++;
                switch (i) {
                    case 0:
                        pDialog.getProgressHelper().setBarColor(getResources().getColor(R.color.purple_200));
                        break;
                    case 1:
                        pDialog.getProgressHelper().setBarColor(getResources().getColor(R.color.purple_500));
                        break;
                    case 2:
                        pDialog.getProgressHelper().setBarColor(getResources().getColor(R.color.purple_700));
                        break;
                    case 3:
                        pDialog.getProgressHelper().setBarColor(getResources().getColor(R.color.teal_200));
                        break;
                    case 4:
                        pDialog.getProgressHelper().setBarColor(getResources().getColor(R.color.teal_700));
                        break;
                    case 5:
                        pDialog.getProgressHelper().setBarColor(getResources().getColor(R.color.red));
                        break;
                    case 6:
                        pDialog.getProgressHelper().setBarColor(getResources().getColor(R.color.green));
                        break;
                }
            }

            public void onFinish() {
                i = -1;
                pDialog.setTitleText("Success!")
                        .setConfirmText("OK")
                        .changeAlertType(SweetAlertDialog.SUCCESS_TYPE);
            }
        }.start();
    }

    private void showImageDialog() {
        new SweetAlertDialog(this, SweetAlertDialog.CUSTOM_IMAGE_TYPE)
                .setTitleText("Sweet!")
                .setContentText("Here's a custom image.")
                .setCustomImage(R.drawable.kali)
                .show();
    }

    private void showWarningCancleDialog() {
        new SweetAlertDialog(this, SweetAlertDialog.WARNING_TYPE)
                .setTitleText("Are you sure?")
                .setContentText("Won't be able to recover this file!")
                .setCancelText("No,cancel plx!")
                .setConfirmText("Yes,delete it!")
                .showCancelButton(true)
                .setCancelClickListener(new SweetAlertDialog.OnSweetClickListener() {
                    @Override
                    public void onClick(SweetAlertDialog sDialog) {
                        // reuse previous dialog instance, keep widget user state, reset them if you need
                        sDialog.setTitleText("Cancelled!")
                                .setContentText("Your imaginary file is safe :)")
                                .setConfirmText("OK")
                                .showCancelButton(false)
                                .setCancelClickListener(null)
                                .setConfirmClickListener(null)
                                .changeAlertType(SweetAlertDialog.ERROR_TYPE);

                        // or you can new a SweetAlertDialog to show
                               /* sDialog.dismiss();
                                new SweetAlertDialog(SampleActivity.this, SweetAlertDialog.ERROR_TYPE)
                                        .setTitleText("Cancelled!")
                                        .setContentText("Your imaginary file is safe :)")
                                        .setConfirmText("OK")
                                        .show();*/
                    }
                })
                .setConfirmClickListener(new SweetAlertDialog.OnSweetClickListener() {
                    @Override
                    public void onClick(SweetAlertDialog sDialog) {
                        sDialog.setTitleText("Deleted!")
                                .setContentText("Your imaginary file has been deleted!")
                                .setConfirmText("OK")
                                .showCancelButton(false)
                                .setCancelClickListener(null)
                                .setConfirmClickListener(null)
                                .changeAlertType(SweetAlertDialog.SUCCESS_TYPE);
                    }
                })
                .show();
    }

    private void showWarningConfirmDialog() {
        new SweetAlertDialog(this, SweetAlertDialog.WARNING_TYPE)
                .setTitleText("Are you sure?")
                .setContentText("Won't be able to recover this file!")
                .setConfirmText("Yes,delete it!")
                .setConfirmClickListener(new SweetAlertDialog.OnSweetClickListener() {
                    @Override
                    public void onClick(SweetAlertDialog sDialog) {
                        // reuse previous dialog instance
                        sDialog.setTitleText("Deleted!")
                                .setContentText("Your imaginary file has been deleted!")
                                .setConfirmText("OK")
                                .setConfirmClickListener(null)
                                .changeAlertType(SweetAlertDialog.SUCCESS_TYPE);
                    }
                })
                .show();
    }

    private void showSuccessTextDialog() {
        new SweetAlertDialog(this, SweetAlertDialog.SUCCESS_TYPE)
                .setTitleText("Downloaded!")
                .setContentText("Saved to Downloads Folder")
                .setConfirmText("OK")
                .show();
    }

    private void showErrorTextDialog() {

        SweetAlertDialog sd = new SweetAlertDialog(this, SweetAlertDialog.ERROR_TYPE)
                .setTitleText("Oops...")
                .setContentText("Only Instagram Profile Link Supported");

        sd.setConfirmText("Okay");
        sd.show();
    }

    private void showUnderTextDialog() {

        SweetAlertDialog sd = new SweetAlertDialog(this);
        sd.setContentText("It's pretty, isn't it?");
        sd.setCanceledOnTouchOutside(true);
        sd.show();
    }
}
```

# App Highlight

![Sweet Dialog App1](https://user-images.githubusercontent.com/74413402/192094497-0583538f-cbea-4300-bba9-3149ee9ab78f.png)
![Sweet Dialog App2](https://user-images.githubusercontent.com/74413402/192094503-c306cf6e-0e71-473f-9f38-6b335b460581.png)
![Sweet Dialog App3](https://user-images.githubusercontent.com/74413402/192094505-260afa64-cab2-4f2d-a75a-1287d500ec4f.png)
![Sweet Dialog App5](https://user-images.githubusercontent.com/74413402/192094561-282c66a2-8789-4a2d-be2f-8cd6f123e183.png)
![Sweet Dialog App6](https://user-images.githubusercontent.com/74413402/192094585-00f7badc-e639-4c52-8bfe-9085b7a5777b.png)
![Sweet Dialog App7](https://user-images.githubusercontent.com/74413402/192094588-30a23464-f09c-479d-9584-2276898093aa.png)
![Sweet Dialog App8](https://user-images.githubusercontent.com/74413402/192094592-ee548d7b-d9dc-4a27-a478-7e16dcd4ac2f.png)
![Sweet Dialog Code](https://user-images.githubusercontent.com/74413402/192094594-c81203fd-0b7f-4dc1-8c00-7bf34c356002.png)
