<template>
<div id="app">
        <h2 class="paris">Upload a File - Vuejs API Call</h2>

        <form enctype="multipart/form-data">

            <div class="form-horizontal">
                <hr />

                <div class="form-group">
                    <p class="control-label col-md-2" style="font-family:Poiret One;font-weight:bolder;">Language</p>
                    <div class="col-md-10">
                        <select name="partitionkey">
                            <option value="English">English</option>
                            <option value="Spanish">Spanish</option>
                            <option value="French">French</option>
                            <option value="Chineese">Chineese</option>
                            <option value="Ngambaye">Ngambaye</option>
                        </select><br />
                    </div>
                </div>
                <div class="form-group">
                    <p class="control-label col-md-2" style="font-family:Poiret One;font-weight:bolder;">Book Title</p>
                    <div class="col-md-10">
                        <input type="text" name="title" style="width:80%;" maxlength="200" required>
                    </div>
                </div>
                <div class="form-group">
                    <p class="control-label col-md-2" style="font-family:Poiret One;font-weight:bolder;">Book Text</p>
                    <div class="col-md-10">
                        <textarea rows="5" style="width:80%;" name="body" maxlength="2000" required></textarea>
                    </div>
                </div>
                <div class="form-group">
                    <p class="control-label col-md-2" style="font-family:Poiret One;font-weight:bolder;">Images</p>
                    <div class="col-md-10">
                        <input type="file" multiple="multiple" id="photoUrl" name="file" v-on:change="fileChange($event.target.files)" accept="application/vnd.msword, application/vnd.ms-excel, application/vnd.ms-powerpoint,
                text/plain, application/pdf, image/*">
                    </div>
                </div>
                <div class="form-group">
                    <p class="control-label col-md-2" style="font-family:Poiret One;font-weight:bolder;">Sounds</p>
                    <div class="col-md-10">
                        <input type="file" multiple="multiple" id="photoUrl" name="file" v-on:change="fileChange($event.target.files)" accept="application/vnd.msword, application/vnd.ms-excel, application/vnd.ms-powerpoint,
                text/plain, application/pdf, image/*">
                    </div>
                </div>
                <div class="form-group">
                    <p class="control-label col-md-2" style="font-family:Poiret One;font-weight:bolder;">Book Author</p>
                    <div class="col-md-10">
                        <input type="text" name="custom5" style="width:80%;" maxlength="100" required>
                    </div>
                </div>
                <div class="form-group">
                    <p class="control-label col-md-2" style="font-family:Poiret One;font-weight:bolder;">Tags</p>
                    <div class="col-md-10">
                        <input type="text" name="custom3" style="width:80%;" maxlength="500">
                    </div>
                </div>
            </div>
            <div class="form-group">
                <button type="button" v-on:click="upload()" class="btn btn-primary btn-lg" style="font-family:Poiret One;width:25%;">Submit</button>
            </div>
        </form>
        {{ message }}
    </div>

</template>

<script>
    import axios from "axios";

    export default {
        name: 'app',
        data() {
            return {
                files: new FormData()
            }
        },
        methods: {
            fileChange(fileList) {
                this.files.append("file", fileList[0], fileList[0].name);
            },
            upload() {
                axios({ method: "POST", "url": "http://mekonecampusapi.azurewebsites.net/api/pictures", "data": this.files }).then(result => {
                    console.dir(result.data);
                    message = result.data;
                }, error => {
                    console.error(error);
                });
            }
        }
    }
</script>

<style>
    #app {
    body {
        padding: 20px;
    }

    /* Set padding to keep content from hitting the edges */
    .body-content {
        padding-left: 20px;
        padding-right: 20px;
    }

    /* Override the default bootstrap behavior where horizontal description lists
       will truncate terms that are too long to fit in the left column
    */
    .dl-horizontal dt {
        white-space: normal;
    }

    /* Set width on the form input elements since they're 100% wide by default */
    input,
    select,
    textarea {
        /*max-width: 280px;*/
    }


    input[type=text], input[type=password], textarea, select {
        font-family: 'Roboto', serif;
        width: 90%;
        padding: 12px 20px;
        margin: 8px 0;
        display: inline-block;
        border: 1px solid #ccc;
        border-radius: 4px;
        box-sizing: border-box;
        background-color: #f2f2f2;
    }

    select option {
        background: lightyellow;
    }

    .paris {
        font-family: 'Fahkwang', serif;
        font-size: 20px;
    }

    .bira {
        font-family: 'Fahkwang', serif;
        font-size: 12px;
    }

    .admin {
        font-family: 'Marcellus SC', serif;
        font-size: 20px;
    }

    .adminsmall {
        font-family: 'Marcellus SC', serif;
        font-size: 14px;
    }

    .signature {
        font-family: 'Poiret One', serif;
        font-size: 14px;
    }

    .dash {
        font-family: 'Poiret One', serif;
        font-size: 20px;
        font-weight: 900;
    }

    .signature2 {
        font-family: 'Poiret One', serif;
    }

    .signature3 {
        font-family: 'Poiret One', serif;
        line-height: 150%;
    }

    .foota {
        font-family: 'Fahkwang', serif;
        color: black;
        font-size: 14px;
        text-align: center;
        padding: 2%;
        margin-left: 5%;
        margin-right: 5%;
        border-bottom: 1px solid green;
        border-top: 1px solid green;
        background-color: white;
    }

    .boda {
        color: black;
        font-size: 18px;
        text-align: center;
        padding: 2%;
        margin-left: 1%;
        margin-right: 1%;
        background-color: white;
    }

    .boda2 {
        color: black;
        font-size: 18px;
        text-align: center;
    }

    .partialTitre {
        font-family: 'Marcellus SC', serif;
        font-size: 24px;
        text-shadow: 4px 4px 4px #aaa;
    }

    .auteur {
        font-family: 'Roboto', serif;
        color: #1C5717;
        font-size: 12px;
    }

    .lieu {
        font-family: 'Roboto', serif;
        color: #7F857B;
        font-size: 12px;
        font-style: italic;
    }

    .chapeau {
        font-family: 'Roboto', serif;
        color: black;
        font-size: 16px;
        font-weight: 200;
        text-align: left;
        line-height: 150%;
    }

    .corps {
        font-family: 'Roboto', serif;
        color: black;
        font-size: 14px;
        text-align: left;
        font-weight: 100;
        white-space: pre-wrap;
        line-height: 150%;
    }

    .titre {
        font-family: 'Roboto', serif;
        padding: 0px;
        line-height: 150%;
        font-size: 22px;
    }
    }
</style>
