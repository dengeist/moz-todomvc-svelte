<style>
.c-cb {
  display: inline-block;
	padding-left: 1.5em;
  position: relative;
}

.c-cb > input[type="checkbox"] {
  font: inherit;
	-moz-appearance: none;
	-webkit-appearance: none;
  appearance: none;
  margin: 0;
	margin-top: .75em;
	opacity: .00001;
	position: absolute;
	vertical-align: top;
	z-index: 2;
}

/**
 * Make sure the label is only as wide as the
 * inner text requires it to be.
 * The label should not be a block element
 * or run 100% width of its container.
 * Why would someone expect to click
 * white space on the opposite side of the
 * screen to have a checkbox checked?
 */
.c-cb > label {
	display: inline-block;
  padding: .75em .5em;
}


/**
 * Note, the :before pseudo-element is the new
 * "bounds" or "box" of the checkbox.
 * It must be the same height, width and
 * position of the native checkbox element.
 */
.c-cb > label:before,
.c-cb > input[type="checkbox"] {
	height: 1.125em;
	left: .125em;
  width: 1.125em;
}

/**
 * Base styles for use on both
 * pseudo elements.
 */
.c-cb > label:before,
.c-cb > label:after {
	border: 1px solid;
	content: " ";
	position: absolute;
	transition:
		border-color .2s ease-in-out,
		box-shadow .2s ease-in-out,
		transform .2s ease-in-out;
}

/**
 * Styles for the custom box boundary.
 */
.c-cb > label:before {
  position: absolute;
	border-color: #565656;
  box-shadow: 0 0 0 1px #565656;
	width: 1.125em;
	height: 1.125em;
	left: .125em;
	top: .825em;
}

/**
 * This recreates the "check" mark.
 */
.c-cb > label:after {
  position: absolute;
	border: 0;
	border-bottom: 4px solid #565656;
	border-right: 4px solid #565656;
	height: .85em;
	left: .425em;
	top: .85em;
	transform-origin: center center;
	transform: rotate(45deg) scale(0);
	width: .5em;
}

.c-cb > label {
  width: unset;
}

/**
 * ** Defining States **
 */
.c-cb > input:checked ~ label:before {
	border-color: transparent;
	box-shadow: 0 0 0 2px #0d5192;
}

.c-cb > input:focus ~ label:before {
	border-color: transparent;
	box-shadow: 0 0 0 2px #228BEC;
	outline: 2px dashed #228BEC;
	outline-offset: 4px;
}

.c-cb > input:checked ~ label:after {
	transform: rotate(45deg) scale(0.8);
}

.c-cb > input:checked:focus ~ label:after {
	border-color: #228BEC;
}

.c-cb > input[disabled] ~ label {
	opacity: .625;
}

/* placeholder design until a better required
   design pattern can be created */
.c-cb > input:invalid ~ label:before {
	border-color: #f00;
	box-shadow: 0 0 0 1px #f00;
}

.c-cb > input:invalid:focus ~ label:before {
	box-shadow: 0 0 0 2px #f00;
}
.btn-group {
  float: right;
  margin-top: 12px;
  
}
</style>

<li class="todo">
  <div class="c-cb">
    <input id="todo-toggle-foo" class="todo-toggle" type="checkbox" checked/>
    <label class="todo-text" for="todo-toggle-foo">An item</label>
  </div>
  <div class="btn-group">
    <button type="button" class="btn todo-edit">Edit</button>
    <button type="button" class="btn btn__danger todo-delete">Destroy</button>
  </div>
</li>