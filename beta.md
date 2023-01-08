---
layout: default
title: Testing Builds Downloads
---
<div class="card shishu-light-bg z-depth-3">
  <div class="card-content">
    <span class="card-title">These build are made for testing...</span>
    <p>... And that's all you have to do, If you flash a broken build, the only one to blame is you. All the releases listed on here are experimental builds made by our official maintainers, but for complete testing purposes.</p> <p>Don't pull a Xiaomi Global Beta on us and if you have issues, please let us know with a log or with a proper report. Screenshots and messages telling what isn't working will be ignored completely.</p>
  </div>
</div>
<div class="card shishu-light-bg z-depth-3">
  <div class="card-content">
    <span class="card-title">Releases</span>
    <ul class="collapsible shishu-lighter-bg collapsible-noborder">
      {% for device in site.devicesbeta %}
        {% if device.maintainer %}
        <li>
          <div class="collapsible-header collapsible-noborder shishu-lighter-bg">
            <i class="material-icons">phone_android</i>
          {{ device.codename }} | {{ device.fullname }}</div>
          <div class="collapsible-body collapsible-noborder shishu-midlight-bg">
            <span>Maintainer:</span><div class="chip shishu-lighter-bg" style="margin-left:4px">{{ device.maintainer }}</div><br>
            <span>Latest build:</span><div class="chip shishu-lighter-bg" style="margin-left:4px">{{ device.filename }}</div><br>
            {% if device.newformat %}
            <span>Build size:</span><div class="chip shishu-lighter-bg" style="margin-left:4px">{{ device.buildsize | divided_by: 1048576 }}MB</div><br><br>
            {% else %}
            <span>Build size:</span><div class="chip shishu-lighter-bg" style="margin-left:4px">{{ device.buildsize }}</div><br><br>
            {% endif %}
            {% if device.notes %}
              <span>Notes:</span><div class="chip shishu-lighter-bg" style="margin-left:4px">{{ device.notes }}</div><br><br>
            {% endif %}
            <a class="waves-effect waves-light btn-small shishu-accent-btn" href="https://sourceforge.net/projects/bootleggersrom/files/builds/{{ device.codename }}/beta/{{ device.filename }}"><i class="material-icons left">get_app</i>Download</a>
            {% if device.mirrorlink %}
              <a class="waves-effect waves-light btn-small shishu-accent-btn" href="{{ device.mirrorlink }}"><i class="material-icons left">open_in_new</i>Mirror</a>
            {% endif %}
            <a class="waves-effect waves-light btn-small shishu-accent-btn" href="https://sourceforge.net/projects/bootleggersrom/files/builds/{{ device.codename }}/beta"><i class="material-icons left">history</i>Older Builds</a>
            <a class="waves-effect waves-light btn-small shishu-accent-btn modal-trigger" href="#modal-chlg-{{device.codename}}"><i class="material-icons left">receipt</i>Changelog</a>
          </div>
        </li>
        {% endif %}
        <!-- Modal for {{device.codename}} -->
        <div id="modal-chlg-{{device.codename}}" class="modal modal-fixed-footer shishu-light-bg">
          <div class="modal-content">
              <h4>Changelog for {{ device.codename }}</h4>
              <div class="chlg-code cl-code-{{ device.codename }}"></div>
          </div>
          <div class="modal-footer shishu-light-bg">
            <a href="#!" class="modal-close waves-effect waves-light btn-flat">Close</a>
          </div>
        </div>
       <script>
        $(document).ready(function(){
         $('#modal-chlg-{{device.codename}}').modal(
           {onOpenEnd: getChangelogBeta('{{device.codename}}')
           });
         });
       </script>
      {% endfor %}
    </ul>
  </div>
</div>