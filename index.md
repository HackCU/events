---
title: Home
layout: base
---


<section class="events">
    <div class="container">
        <div class="row">
            <h1 class="text-center white-text biko main-title">Our events</h1>
            {% assign sorted = site.data.events | sort: 'date','last' %}
            {% for event in sorted %}               
                <div class="col-sm-6 col-md-4">
                    <a {% unless event.url == null %} href="{{event.url}}" {% endunless %} target="_blank" class="event-url">
                        <div class="panel panel-default ">
                            <div class="panel-heading">
                                <span class="past-text biko">PAST</span>
                                {% if event.image-url %}<img class="img-responsive {% unless event.light_background == null %}light_background{% endunless %}" src="{{event.image-url}}">{%endif%}
                                <h4 class="event-name biko {% unless event.light_background == null %}light_background{% endunless %}" >{{event.name}}</h4>
                            </div>
                            <div class="panel-body event" data-date="{{ event.date }}">                                
                                <p>{{event.line}}</p>
                            </div>
                            <div class="panel-footer">
                                {{event.date |  date: "%b %-d %Y" }} {% unless event.location == null or event.date == null  %}at{% endunless %} {{event.location}}
                            </div>
                        </div>
                    </a>
                </div>
            {% endfor %}
        </div>
        <div class="row text-center">
            <div class="email-sub col-md-4 col-md-offset-4">
                <a class="btn btn-accent calendar biko" href="https://calendar.google.com/calendar/r?cid=webcal://{{ site.domain }}/calendars/events.ics" target="_blank">Add events to Google Calendar</a>
                {% include email.html %}
            </div>
        </div>
    </div>
</section>
