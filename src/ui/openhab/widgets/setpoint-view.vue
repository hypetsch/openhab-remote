<script lang="ts">
    import {Component} from "vue-property-decorator";
    import WidgetControl from "./widget-control";
    import {ListLabel} from "@app/ui/components";
    import {Icon} from "@app/svg";
    import {Location} from "vue-router";

    @Component({
        components: {ListLabel, Icon}
    })
    export default class SetpointView extends WidgetControl {

        get link(): Location {
            return {
                params: {
                    widgetId: this.widget.widgetId
                }
            };
        }

        get setpointState(): string {
            return this.stateLabel || this.item.state;
        }
    }

</script>

<template>
    <router-link :to="link" class="list-control ripple-effect">
        <list-label :label="label" :state="setpointState">
            <icon type="volume"></icon>
        </list-label>
    </router-link>
</template>
