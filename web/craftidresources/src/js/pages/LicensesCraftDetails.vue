<template>
    <div>
        <license-details :license="license"></license-details>

        <div class="card mb-3">
            <div class="card-header">
                Attached Plugin Licenses
            </div>

            <div class="card-body">

                <license-table type="plugins" :licenses="attachedPluginLicenses"></license-table>

            </div>
        </div>

        <invoices></invoices>

        <div class="card border-danger mb-3">
            <div class="card-header text-white bg-danger">Danger Zone</div>
            <div class="card-body">
                <h5>Unlock license</h5>
                <p>Unlock this license to make it ready for transfer to another domain.</p>
                <div><a class="btn btn-outline-danger" href="#">Unlock License</a></div>

                <hr>

                <h5>Transfer ownership</h5>
                <p>Transfer this license to another Craft ID.</p>
                <div><a class="btn btn-outline-danger" href="#">Transfer License</a></div>
            </div>
        </div>
    </div>
</template>

<script>
    import { mapGetters } from 'vuex'
    import LicenseDetails from '../components/LicenseDetails'
    import LicenseTable from '../components/LicenseTable';
    import Invoices from '../components/Invoices';

    export default {

        components: {
            LicenseDetails,
            LicenseTable,
            Invoices,
        },

        computed: {

            ...mapGetters({
                craftLicenses: 'craftLicenses',
                pluginLicenses: 'pluginLicenses',
            }),

            license() {
                return this.craftLicenses.find(l => l.id == this.$route.params.id);
            },

            attachedPluginLicenses() {
                return this.pluginLicenses;
            }
        }

    }
</script>
